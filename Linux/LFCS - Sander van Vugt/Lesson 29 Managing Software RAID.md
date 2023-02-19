![[M13.png]]

1. Create a RAID 5 device, using 3 devices of 1 GB each.  Also allocate an additonal device as spare device
2. Put a file system on it and mount it on /raid
3. fail one of the devices, monitor what is happening
4. Replace the failed device with the spare device
5. Answers:
	1. mdadm --create /dev/md0--level=5 --raid-disks=3 --spare-devices=1 /dev/xvdd1 /dev/xvdd2 /dev/xvdd3 /dev/xvdd4
	2. mdadm --fail /dev/md0 /dev/xvdd1
	3. mdadm --remove /dev/md0 /dev/xvdd1 [after failure]
	4. mdadm --add /dev/md0 /dev/xvd4
