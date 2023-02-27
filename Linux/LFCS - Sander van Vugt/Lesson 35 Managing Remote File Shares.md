![[M19.png]]

1. On one server, configure Samba to share a directory /samba.  Also, configure NFS to share a directory /files
2. Answers:
3. on Server: ubuntu
	1. apt install nfs-kernel-server
	2. apt install samba -y
	3. apt isntall samba-common -y
	4. ufw allow Samba
	5. nfw allow nfs
	6. mkdir /files
	7. mkdir /samba
	8. vi /etc/exports
		1. /files *(rw,no_root_squash)
	9. vi /etc/samba/smb.conf
		1. [samba]
		2.  path = /samba
		3.  writable = yes
		4.  allow users = lisa
	10. smbpasswd -a lisa [enter password]
	11. systemctl enable nfs-kernel-server
	12. systemctl enable smbd
4. on client: (centos)
	1. showmount -e ubuntu [export list for ubuntu: /files *]
	2. smbclient  -L ubuntu [samba password i.e. lisa]
		1. yum install cifs-utils samba-client [if it is needed to be installed]
	3. vi etc/fstab
		1. data:/files /files nfs _netdev 0 0 
		2. //data/samba /samba cifs _netdev,username=lisa,password=password 0 0
		3. ubuntu:/files /files nfs _netdev 0 0 
		4. //ubuntu/samba /samba cifs _netdev,username=lisa,password=password 0 0
	4. mkdir /samba
	5. mkdir /files
	6. then mount the /samba & /files [he uses the automated way] on the server by the looks as the previous etc/fstab data is not in the file but is showing as root@centos??? not sure why he has edited the same etc/fstab file on the same system twice...
		1. vi etc/fstab
			1. ubuntu:/files /files nfs _netdev 0 0
			2. //ubuntu/samba /samba cifs _netdev,username=lisa,password=password 0 0