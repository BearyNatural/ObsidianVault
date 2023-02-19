![[M6.png]]

1. Request a list of currently loaded Linux kernel modules
	1. lsmod | less 
2. Load the module for vfat support; does it have any dependencies?
	1. modprobe vfat [vfat is a dependency of the fat module]
	2. lsmod | grep vfat [this shows no output for my ubuntu ec2]
		1. modinfo vfat [shows it is there and builtin]
3. Unload this module again
	4. modprobe -r vfat [to unload it]
		1. My ubuntu ec2 output: [modprobe: FATAL: Module vfat is builtin.]
		2. lsmod | grep vfat
4. Make sure your system can be used to forward IP packets
	1. sysctl -a | grep forward [shows lots of parameters, the one we need is net.ipv4.ip_forward]
		1. mine shows: [net.ipv4.ip_forward = 0]
		2. we need change the 0 to 1 to enable packet forwarding
		3. vi /etc/sysctl.conf
			1. line 28 - #net.ipv4.ip_forward=1 [just needs to uncomment this line to enable packet forwarding]