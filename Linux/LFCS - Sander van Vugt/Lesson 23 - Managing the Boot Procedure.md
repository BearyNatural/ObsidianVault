![[M7.png]]

1. Set the GRUB boot timeout to 5 seconds 
2. Ensure the none of the silent options are used to hide startup messages while booting  your system
3. Answers:
	1. vi /etc/default/grub
		1. change: GRUB_TIMEOUT=0 to GRUB_TIMEOUT=5
	2. run the following command to redirect the output
		1. grub-mkconfig -o /boot/grub2/grub.cfg
			2. this command errored for me: [
			   Sourcing file `/etc/default/grub'
			Sourcing file `/etc/default/grub.d/40-force-partuuid.cfg'
			Sourcing file `/etc/default/grub.d/50-cloudimg-settings.cfg'
			Sourcing file `/etc/default/grub.d/init-select.cfg'
			/usr/sbin/grub-mkconfig: 275: cannot create /boot/grub2/grub.cfg.new: Directory nonexistent]
	1. reboot