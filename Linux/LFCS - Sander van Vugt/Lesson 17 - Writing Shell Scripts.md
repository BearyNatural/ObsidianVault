![[M1.png]]

1. A customer has exported a long list of LDAP user names.  These usernames are stored in the file ldapusers.  In this file, every user has a name in the format cn=list,dc=example,dc=com.  Write a script that extracts the username only (lisa) from all of these lines and write those to a new file
	1. see user script below [lesson.sh]
	2. cat ldapusers
		1. cn=lisa,dc=example,dc=com
		2. cn=amy,dc=example,dc=com
	3. chmod u+x lesson.sh
	4. ./lesson.sh

[lesson.sh]
#!/bin/bash
#extract the user names
for i in $(cat ldapusers)
do
	USER=${1%%,*}
	USER=${USER#*=}
	echo $USER >> users
done

#show that user creation will work
for j in $(cat users)
do
	echo useradd $j
done