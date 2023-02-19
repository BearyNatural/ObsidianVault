![[M19.png]]

1. On one server, configure Samba to share a directory /samba.  Also, configure NFS to share a directory /files
2. Answers:
3. on Server:
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
4. on client:
	1. showmount -e ubuntu [export list for ubuntu: /files *]
	2. smbclient  -L ubuntu [samba password i.e. lisa]
	3. vi etc/fstab
		1. data:/files /files nfs _netdev 0 0 
		2. //data/samba /samba cifs _netdev,username=lisa,password=password 0 0
		3. ubuntu:/files /files nfs _netdev 0 0 
		4. //ubuntu/samba /samba cifs _netdev,username=lisa,password=password 0 0
	4. mkdir /samba
	5. mkdir /files
	6. then mount the /samba & /files [he uses the automated way]