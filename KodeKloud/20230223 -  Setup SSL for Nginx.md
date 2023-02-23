The system admins team of `xFusionCorp Industries` needs to deploy a new application on `App Server 1` in `Stratos Datacenter`. They have some pre-requites to get ready that server for application deployment. Prepare the server as per requirements shared below:
1.  Install and configure `nginx` on `App Server 1`.    
2.  On `App Server 1` there is a self signed SSL certificate and key present at location `/tmp/nautilus.crt` and `/tmp/nautilus.key`. Move them to some appropriate location and deploy the same in Nginx.    
3.  Create an `index.html` file with content `Welcome!` under Nginx document root.    
4.  For final testing try to access the `App Server 1` link (either hostname or IP) from `jump host` using curl command. For example `curl -Ik https://<app-server-ip>/`.

stapp01
172.16.238.10
stapp01.stratos.xfusioncorp.com
tony
Ir0nM@n
Nautilus App 1

%% stapp01 %% Ir0nM@n
ssh tony@stapp01 
sudo -i
yum install epel-release -y [need to this before nginx]
yum install nginx -y
mv /tmp/nautilus.crt /etc/pki/CA/certs/nautilus.crt
mv /tmp/nautilus.ke /etc/pki/CA/private/nautilus.key
ll /tmp/
find /etc -type f -name '.conf' | grep nginx
vi /etc/nginx/nginx.conf
        **ssl_certificate "/etc/pki/CA/certs/nautilus.crt";**
        **ssl_certificate_key "/etc/pki/CA/private/nautilus.key";**

