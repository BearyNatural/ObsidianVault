The system admins team of `xFusionCorp Industries` needs to deploy a new application on `App Server 3` in `Stratos Datacenter`. They have some pre-requites to get ready that server for application deployment. Prepare the server as per requirements shared below:
1.  Install and configure `nginx` on `App Server 3`.    
2.  On `App Server 3` there is a self signed SSL certificate and key present at location `/tmp/nautilus.crt` and `/tmp/nautilus.key`. Move them to some appropriate location and deploy the same in Nginx.    
3.  Create an `index.html` file with content `Welcome!` under Nginx document root.    
4.  For final testing try to access the `App Server 3` link (either hostname or IP) from `jump host` using curl command. For example `curl -Ik https://<app-server-ip>/`.

stapp03
172.16.238.12
stapp01.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% stapp03 %% BigGr33n
ssh banner@stapp03 
sudo -i
yum install epel-release -y [need to this before nginx]
yum install nginx -y

find /etc -type f -name '.conf' | grep nginx
vi /etc/nginx/nginx.conf [at the bottom of doc take note of where the crt & key are required, change the name, uncomment that block and the next html error block]
		Server_Name 172.16.238.12
        ssl_certificate "/etc/pki/nginx/nautilus.crt";
        ssl_certificate_key "/etc/pki/nginx/private/nautilus.key";

ll /tmp/
mkdir -p /etc/pki/nginx/nautilus
cp /tmp/nautilus.crt /etc/pki/nginx/nautilus.crt
cp /tmp/nautilus.key /etc/pki/nginx/private/nautilus.key

cat /etc/nginx/nginx.conf | grep html [root         /usr/share/nginx/html;]
ll /usr/share/nginx/html
vi /usr/share/nginx/html/index.html [Welcome!'']
rm /usr/share/nginx/html/index.html [won't let me edit it :O ]

systemctl start nginx
systemctl status nginx

yum install curl -y
curl https://172.16.238.12
[curl: (60) Peer's certificate issuer has been marked as not trusted by the user.
More details here: http://curl.haxx.se/docs/sslcerts.html
curl performs SSL certificate verification by default, using a "bundle"
 of Certificate Authority (CA) public keys (CA certs). If the default
 bundle file isn't adequate, you can specify an alternate file
 using the --cacert option.
If this HTTPS server uses a certificate signed by a CA represented in
 the bundle, the certificate verification probably failed due to a
 problem with the certificate (it might be expired, or the name might
 not match the domain name in the URL).
If you'd like to turn off curl's verification of the certificate, use
 the -k (or --insecure) option.]


even though the certificate complained about being expired it still passed as a complete