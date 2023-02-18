![[M2.png]]

1. Configure your system such that /etc/securetty will apply to sessions that are opened with su, but consider /dev/tty4 as insecure, and block any attempt to log in as root from there.
	1. cat /etc/securetty [list of terminal considered secure - not in ubuntu ec2]
		1. dd to delete tty4 line[save and exit out]
	2. cat /etc/pam.d/login line 24
		1. cat /etc/pam.d/login | head -n 24 | tail -n 1
		2. session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close