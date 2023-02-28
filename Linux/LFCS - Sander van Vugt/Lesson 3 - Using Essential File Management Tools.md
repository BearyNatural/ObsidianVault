![[L3 1.png]]

1. Create a directory structure /tmp/files/pictures, /tmp/files/photos and /tmp/files/videos
	1. mkdir -p /tmp/files/pictures /tmp/files/photos /tmp/files/videos
2. Copy all files that have a name starting with an a, b, or c from /etc to /tmp/files
	1. cp /etc/[a-c]* /tmp/files
3. from /tmp/files, move all files that have a name starting with an a or b to /tmp/files/photos, and files with a name starting with a c to /tmp/files/videos
	1. mv /tmp/files/[ab]* /tmp/files/photos
	2. mv /tmp/files/[c]* /tmp/files/videos
4. find all files in /etc that have a size smaller than 1000b and copy those to /tmp/files/pictures
	1. find /etc/ -type f -size -1000c -exec cp {} /tmp/files/pictures/ \; [use c not b]
5. In /tmp/files, create a symbolic link to /var
	1. ln -s /var /tmp/files 
		1. to check /var [lrwxrwxrwx  1 root root     4 Feb 18 07:01 var -> /var/]
6. Create a compressed archive file of the /home directory
	1. cd /tmp/files
	2. tar -czvf home.tgz /home [t for tar, gz for compressed with gz utility] (z needs to be before f otherwise it will error)
7. Extract this compressed archive file with relative file names in /tmp/archive
	1. mkdir /tmp/archive
	2. tar -xvf home.tgz -C /tmp/archive/ [-C for where you want it sent to]
	3. ls /tmp/archive
	4. tree /tmp/archive

- find all files that have the `executable` permission bit enabled for the `user` that owns them
	- find / -type f -perm /u+x