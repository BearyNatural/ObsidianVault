Login
sudo -i [or sudo su -]
mkdir /home/[dirname]
mkdir /home/[dirname]/{bin, lib64}
groupadd [groupname]
useradd -g [groupname] username
passwd [username] - enter a new password
groups [username] - to confirm what groups user is in
cd /home/[dirname]/bin/
cp /usr/bin/ls .
cp /usr/bin/bash .
ldd /bin/bash [command used to find all the libraries behind the above 2 commands] then copy them over with the following command
cp -v [copy and paste the output from the above here]
ldd /bin/ls [same as the bash command above]
cp -v [same as the above cp/paste the output from the last command]
cd .. & pwd to confirm
vim escapeplan.txt [echo: All you have to do is open the door!]
chroot /home/[dirname]/ /bin/bash - command used to create the environment - the following is playing around you can't actually do anything :'()'
ls cat escapeplan.txt pwd cd .. cd .. pwd exit
vim /etc/ssh/sshd_config [insert the following at the bottom of the page]
Match group [groupname]
					ChrootDirectory /home/[dirname]/
					X11Forwarding no
					AllowTcpForwarding no
systemctl restart sshd [restarts so that the system will read the above changes and put the user in the dirname directory rather than root]
ssh [username]@IP - enter password for user that you set



 



# Main Deployment Configurations

At a high level, you have four main deployment configurations:

-   **Single-node**  
    With a single-node deployment, all the components run on the same server. This is great for testing, learning, and developing around Kubernetes.
-   **Single head node, multiple workers**  
    Adding more workers, a single head node and multiple workers typically will consist of a single node etcd instance running on the head node with the API, the scheduler, and the controller-manager.
-   **Multiple head nodes with HA, multiple workers**  
    Multiple head nodes in an HA configuration and multiple workers add more durability to the cluster. The API server will be fronted by a load balancer, the scheduler and the controller-manager will elect a leader (which is configured via flags). The etcd setup can still be single node.
-   **HA etcd, HA head nodes, multiple workers**  
    The most advanced and resilient setup would be an HA etcd cluster, with HA head nodes and multiple workers. Also, etcd would run as a true cluster, which would provide HA and would run on nodes separate from the Kubernetes head nodes.

Which of the four you will use will depend on how advanced you are in your Kubernetes journey, but also on what your goals are.

The use of Kubernetes Federation also offers high availability. Multiple clusters are joined together with a common control plane allowing movement of resources from one cluster to another administratively or after failure.​ While Federation has has some issues, there is hope [v2](https://github.com/kubernetes-sigs/Kubefed) will be a stronger product.

API - Application Programming Interface - a set of definitions and protocols to build and integrate application software.

In the resources section of the **PodSpec** you can pass parameters which will be passed to the container runtime on the scheduled node:
resources:
  limits: 
    cpu: "1"
    memory: "4Gi" 
  requests:
    cpu: "0.5"
    memory: "500Mi"

The code below will run the init container until the ls command succeeds; then the database container will start.

spec:
  containers:
  - name: main-app
    image: databaseD 
  initContainers:
  - name: wait-database
    image: busybox
    command: ['sh', '-c', 'until ls /db/dir ; do sleep 5; done; '] 

With Container Network Interface (CNI), you can write a network configuration file:

**{  
    "cniVersion": "0.2.0",  
    "name": "mynet",**    **"type": "bridge",  
    "bridge": "cni0",  
    "isGateway": true,  
    "ipMasq": true,  
    "ipam": {  
        "type": "host-local",  
        "subnet": "10.22.0.0/16",  
        "routes": [  
            { "dst": "0.0.0.0/0" }  
             ]  
     }  
}**

This configuration defines a standard Linux bridge named **cni0**, which will give out IP addresses in the subnet 10.22.0.0./16. The bridge plugin will configure the network interfaces in the correct namespaces to define the container network properly.

pod-to-pod communication across nodes.

The requirement from Kubernetes is the following:

-   All pods can communicate with each other across nodes.
-   All nodes can communicate with all pods.
-   No Network Address Translation (NAT).

Basically, all IPs involved (nodes and pods) are routable without NAT. This can be achieved at the physical network infrastructure if you have access to it (e.g. GKE). Or, this can be achieved with a software defined overlay with solutions like:

-   Weave
-   Flannel
-   Calico
-   Romana​.

What really sets Kubernetes apart is its features oriented towards fault-tolerance, self-discovery, and scaling, coupled with a mindset that is purely API-driven.

**$ curl --cert userbob.pem --key userBob-key.pem \    
--cacert /path/to/ca.pem \     
https://k8sServer:6443/api/v1/pods**

The following shows what user **bob** could do in the **default** namespace and the **developer** namespace, using the **auth can-i** subcommand to query (commands and outputs): 

**$ kubectl auth can-i create deployments  
****yes** 

**$ kubectl auth can-i create deployments --as bob  
****no** 

**$ kubectl auth can-i create deployments --as bob --namespace developer  
****yes**

For example, to annotate only Pods within a namespace, you can overwrite the annotation, and finally delete it. See the following commands:

**$ kubectl annotate pods --all description='Production Pods' -n prod** 

**$ kubectl annotate --overwrite pod webpod description="Old Production Pods" -n prod** 

**$ kubectl -n prod annotate pod webpod description-**

Below is an example of a simple pod manifest in YAML format. You can see the **apiVersion** (it must match the existing API group), the **kind** (the type of object to create), the **metadata** (at least a name), and its **spec** (what to create and parameters), which define the container that actually runs in this pod:

**apiVersion: v1  
kind: Pod  
metadata:  
    name: firstpod  
spec:  
    containers:  
    - image: nginx  
      name: stan** 

You can use the **kubectl create** command to create this pod in Kubernetes. Once it is created, you can check its status with **kubectl get pods**. The output is omitted to save space: 

**$ kubectl create -f simple.yaml** 

**$ kubectl get pods** 

**$ kubectl get pod firstpod -o yaml** 

**$ kubectl get pod firstpod -o json**

Should you want to see all the resources on a system, you must pass the **--all-namespaces** option to the **kubectl** command.

**kubectl get ns**

kubectl create ns linuxcon

kubectl describe ns linuxcon

kubectl get ns/linuxcon -o yaml

kubectl delete ns/linuxcon

All API resources exposed are available via **kubectl**. To get more information, do **kubectl help**.

kubectl command type Name flag 

**​$ curl https://localhost:6443/apis --header "Authorization: Bearer $token" -k**

As usual, you get all the CRUD operations via **kubectl** command: ​

**$ kubectl get daemonsets**

**$ kubectl get ds**

**kubectl get deployments,rs,pods -o json**
**kubectl get deployments,rs,pods -o yaml**

**$ kubectl get pv**

**$ kubectl get pvc**

kube-apiserver --enable-aggregator-routing=true

The type of authentication used is defined in the kube-apiserver startup options. Below are four examples of a subset of configuration options that would need to be set depending on what choice of authentication mechanism you choose:

**--basic-auth-file**

**--oidc-issuer-url**

**--token-auth-file**

**--authorization-webhook-config-file**

