![[L2 1.png]]

1. Find out which version of the kernel your computer is using
	1. man -k [most important]
	2. man -k kernel
	3. man uname
	4. uname -a [prints all information for your system]
2. Use man and related resources to find out how to change the hostname of your computer
	1. man hostname [too general, mainly about printing hostname]
	2. man -k hostname
		1. hostnamectl [control the system hostname]
		2. hostnamectl --help
3. Read the help output for lvcreate and find which options must be used
	1. lvcreate --help | less
		1. all the option that are in square brackets [are optional]

