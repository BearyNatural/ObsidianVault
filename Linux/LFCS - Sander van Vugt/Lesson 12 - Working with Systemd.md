![[L12 1.png]]

1. Examine the contents of the sshd service
	1. systemctl cat sshd.service 
	2. other:
		1. cat /etc/ssh/sshd_config [banner, password authentication etc]
2. Ensure the sshd service will be automatically started after a reboot
	1. systemctl status sshd [if it says enabled then it will always automatically restart after reboot]
3. Find out what is used as the default target 
	1. systemctl get-default [shows what runlevel it is set for]
		1. systemctl set-default ...[to change to another runlevel]
4. Show a list of all active unit files
	1. systemctl list-units