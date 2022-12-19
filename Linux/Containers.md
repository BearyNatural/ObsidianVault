
https://github.com/nextcloud
https://www.portainer.io/
https://start.spring.io/
https://www.jenkins.io/download/

docker ps
docker volume create portainer_data
docker volume ls
docker volume command
docker volume inspect nextcloud
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v
portainer_data:/data portainer/portainer
watch docker ps
docker container run -idt -P -v nextcloud:/var/www/html nextcloud
docker logs ac69
docker logs -f ac69
docker volume create portainer_data
docker volume inspect portainer_data
docker stop redis
docker start redis
docker run redis
docker rm [-f]
docker container prune
docker image rm
git config --help
git config --global user.name "Your Name"
git config --glabal user.email "your@email.com"
git config -l
ls ~/.gitconfig
cat ~/.gitconfig
git config --global core.editor vim
git config -e --global
cd ~/learn/ci-cd
ci-cd mv ~/Downloads/hellocd.zip .
ci-cd unzip hellocd.zip

ci-cd cd hellocd
tree
ls -al [ll -a]
git init .
[hellocd git:(master) x] git status
tree .git/
git add pom.xml [adding tracking to file listed under ls -al]
git commit
git log
git add src [adding a directory]
git add [to commit all / add all just like in coding the star]

3 trees of git [working, staging, commit]
git commit -am [file name]

git branch --list
git checkout -b webapp

git status tree

LFS261 - CH 5 - Collaborating and Syncing Changes with Remotes
git remote --help
git remote show [will show]
**in GitConsole**: 
create new repository
name it [description not required]
public
add a README file
choose a license [license: GNU General Public License]
**in CLI**: [create new repository] create it in the console 1st :'()'
echo "# hellocd" >> README.md
git init -b main [Initialize the local directory as a Git repository]
git add . [Adds the files in the local repository and stages them for commit. To unstage a file, use 'git reset HEAD YOUR-FILE'.]
git add README.md
git commit -m "first commit" [Commits the tracked changes and prepares them to be pushed to a remote repository. To remove this commit and modify the file, use 'git reset --soft HEAD~1' and commit and add the file again.]
git remote add origin https://github.com/kayhoweaws/hellocd.git [Sets the new remote]
git remote -v [verifies the new remote URL]
git push -u origin master
**in CLI**: [push an existing repository from the command line]
git remote add origin https://github.com/kayhoweaws/hellocd.git
git push -u origin master

authentication issues:
https://stackoverflow.com/questions/17659206/git-push-results-in-authentication-failed
- response - update ~/.gitconfig
protocol 'fatal: https' is not supported:
https://stackoverflow.com/questions/53988638/git-fatal-protocol-https-is-not-supported
- response - updated  ~/.gitconfig again
repository not found
https://stackoverflow.com/questions/58544631/git-push-error-repository-not-found-even-though-remote-url-is-added + course video 
- need to create respository in the console 1st
- response - updated above procedures

git remote show

Policies
git status [shows if modified]
git diff [can't remember what for]

pipeline{}
	agent{}
	triggers{}
	tools{}
	stages ('Build'/'Test'/'Production') {
			steps}
	post{
		always}
}

Jenkins [https://www.jenkins.io/doc/]
node = scripted pipeline
pipeline = declarative pipeline

Kubs
Helm
spinnaker CI-CD blue/green VM

LFS258
https://training.linuxfoundation.org/cm/LFS258/LabSetup-AWS.mp4
The user ID is **LFtraining** and the password is **Penguin2014**.
https://training.linuxfoundation.org/cm/LFS258/ExpressLearning1.mp4
https://training.linuxfoundation.org/cm/LFS258/HowToUsePutty.mp4

**Dark blue: text typed at the command line**
**Green: Output**
**Black: file content**
**Brown: File/Directory names**
**Light blue: Hyperlink**

Chaos Monkey

[Docker Swarm](https://docs.docker.com/swarm/) is the solution provided by Docker Inc. It has been re-architected recently and is based on [SwarmKit](https://github.com/docker/swarmkit). It is embedded with the Docker Engine.

[Apache Mesos](http://mesos.apache.org/) is a data center scheduler, which can run containers through the use of _frameworks_. [Marathon](https://mesosphere.github.io/marathon/) is the framework that lets you orchestrate containers.

[Nomad](https://www.nomadproject.io/) from HashiCorp, the makers of Vagrant and Consul, is another solution for managing containerized applications. Nomad schedules tasks defined in _Jobs_. It has a Docker driver which lets you define a running container as a task.

[Rancher](https://rancher.com/) is a container orchestrator-agnostic system, which provides a single pane of glass interface to manage applications. It supports Mesos, Swarm, Kubernetes.

12 factor application principles. 
These principles provide great guidance to build web applications that can scale easily, can be deployed in the cloud, and whose build is automated.

![[Pasted image 20221101162326.png]]

Our labs will focus on the use of **kubeadm** and **kubectl**, which are very powerful and complex tools.

**kubectl**
**kubeadm** - **kubeadm init** - **kubeadm join**
**kubectl config use-context foobar**
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/

