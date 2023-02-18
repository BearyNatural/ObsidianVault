![[L6 1.png]]

1. Modify your environment so that after login, all users have access to the following:
	1. An alias with the name ipconfig that runs the op addr show command 
	2. A variable with the name COLOUR that is set to the value red 
	3. Ensure the alias is available in subshells also
	4. Answers:
		1. cd /etc/profile.d/
		2. vi kaylene.sh
			1. alias ipconfig='ip addr show'
			2. export COLOUR=red
		3. useradd -m emily
		4. su - emily
		5. echo $COLOUR [this responds with the preset 'red', this doesn't do anything it is just a variable we have now set]
		6. alias [shows the alias ipconfig is there]
		7. bash [this converts to emily's bash login]
		8. alias [the alias ipconfig should once again be  there] 