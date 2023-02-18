![[L7 1.png]]

1. Create 4 users: linda, laura, anna & anouk
2. Set their passwords to expire after 60 days
3. Create a group sales and make linda and laura members of that group
4. Create a group account and make anna and anouk jmembers of that group
5. Also create a group users, and make all four users members of that group as a secondary group
6. Use input redirection to set the password for these users to 'password'
7. Ensure all these users get a home directory in /home
8. Answers:
	1. vi /etc/login.defs
		1. change PASS_MAX_DAYS number to 60
	2. vi /etc/defaults/useradd
		1. if you need to change the default home directory
	3. groupadd 
		1. sales
		2. account
		3. users
	4. useradd -m -p password 
		1. linda 
		2. laura 
		3. anna 
		4. anouk
	5. usermod -aG sales, users
		1. linda
		2. laura
	6. usermod -aG 
		1. anna
		2. anouk