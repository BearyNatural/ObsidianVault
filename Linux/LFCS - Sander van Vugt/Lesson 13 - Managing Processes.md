![[L13 1.png]]

1. From a root shell, start three processes dd if=/dev/zero of=/dev/null as a background job 
	1. dd if=/dev/zero of=/dev/null & [2187]
	2. dd if=/dev/zero of=/dev/null & [2188]
	3. dd if=/dev/zero of=/dev/null & [2189]
2. use the appropriate command to show that they are running as expected
	1. jobs
	2. ps aux | grep dd [this one is less neat]
3. Change process priority so that one of these three jobs gets double the amount of CPU resources
	1. renice -n -8 2187 
4. Monitor the processes are running as expected
	1. ps -aux | grep dd
	3. top [this is better as it gives a more accurate view]
5. Terminate all three processes
	1. killall dd [verbosely shows they are all terminated]