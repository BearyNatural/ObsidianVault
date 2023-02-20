Review any topic you have issues with; go over it 3 times;
https://training.linuxfoundation.org/lfcs2022changes/
Operations and Deployment - 25%
- configure kernel parameters, persistent and non-persistent https://www.tecmint.com/change-modify-linux-kernel-runtime-parameters/
- diagnose, identify manage and troublshoot - ps; top; iostat
	- iostat -m -x /dev/sd? 3
	- iotop
- manage crontab -l  
/etc/cront*  
/var/spool/cron

install validate and maintain - dpkg -l https://askubuntu.com/questions/7021/alternatives-to-rpm-qa-and-rpm-ql-in-ubuntu

recover from hardware, os or filessystem - fsck https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/

manage virtual machines;  - virt-host-validate https://nsrc.org/activities/agendas/en/cloud-virtualization/cloud-virt/en/kvm-libvirt/ex-ubuntu-kvm-libvirt.html

containers - docker container list https://hub.qovery.com/guides/tutorial/how-to-connect-to-your-eks-cluster-with-kubectl/ 

mandatory access control - https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_security_guide/sect-virtualization_security_guide-svirt-mac
Permission denied :
/var/log/secure  
 /var/log/messages  
 cd /var/log  
grep selinux -i *
grep permission -i *
ls -larthZ
https://phoenixnap.com/kb/selinux
https://www.thegeekdiary.com/restorecon-command-examples-in-linux/
sudo restorecon FILE
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/sect-security-enhanced_linux-working_with_selinux-selinux_contexts_labeling_files

chcon -t httpd_sys_content_t file-name

https://www.baeldung.com/cs/virtual-memory-vs-swap-space
https://www.youtube.com/watch?v=rUnQ_AJOAVo

user limits
user acls https://help.ubuntu.com/community/FilePermissionsACLs
ldap https://devopsideas.com/installation-configuration-openldap-utilities-ubuntu/

git clone URL  
git pull  
git commit -m “something”  
git status
brush up on configure of k

top iotop htop, cpu memory or disk for troubleshooting

du -shx *


ssl https://www.ibm.com/support/pages/openssl-commands-check-and-verify-your-ssl-certificate-key-and-csr
https://docs.pingidentity.com/r/en-us/solution-guides/htg_use_openssl_to_test_ssl_connectivity
openssl s_client -connect google.com:443 -cipher EXP-RC4-MD5
openssl s_client -connect google.com:443

networking
- configure IPV4 & 6 networking and hostname resolution
	- dig, ping, curl -v [gives you the translation] 
- set and sync system time
	- https://acquia.my.site.com/s/article/360005257154-Use-cURL-s-resolve-option-to-pin-a-request-to-an-IP-address
- monitor & troubleshoot networking
	- mis match - nss clumping https://www.youtube.com/watch?v=J-gnDC6B5eE
	- layer 3 & https://www.youtube.com/watch?v=XMcYwr-yJGA watch this video after the exam;''
- ssh
	- ssh -v user@server
	- ssh -vvv user@server
	- server: side : /var/log/messages /var/log/secure
- briddge & bonding
	- bridge is two networking interfaces joined
	- bonding is active passive or active active
- load balancers (elb) & reverse proxies (waf)
	- ubuntu - https://www.digitalocean.com/community/tutorials/how-to-use-apache-http-server-as-reverse-proxy-using-mod_proxy-extension-ubuntu-20-04