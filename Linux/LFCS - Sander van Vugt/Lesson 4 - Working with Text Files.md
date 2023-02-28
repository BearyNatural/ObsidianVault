![[L4 1.png]]

1. Use head and tail to display the 5th line of the file /etc/passwd
	1. head -n 5 /etc/passwd [1st 5 lines]
	2. head -n 5 /etc/passwd | tail -n 1 [gives you the last line of the top 5 requested]
	3. tail -n 5 /etc/passwd [last 5 lines]
	4. tail -n 5 /etc/passwd | head -n 1 [gives you the 1st line of the last 5 requested]
2. Use sed to display the 5th line of the file /etc/passwd
	1. sed -n 5p /etc/passwd [gives the same as above 1.2 i.e. 5th line]
3. Use Awk in a pipe to filter the 1st column out of the results of the command ps aux
	1. ps -aux | awk '{print $1}'
4. Use grep to show the names of all files in /etc that have lines starting with the text 'root'
	5. cd /etc
	6. grep '^root' * [lines starting with '^' aka carrot]
	7. grep '^root' * 2>/dev/null [this cleans up the result by redirecting using stdout & stderr]
	8. grep -l '^root' * 2>/dev/null [-l lists just the file names and no longer shows contents]
5. Use grep to show all lines from all files in /etc that contain exactly 3 characters
	1. grep '^...$' * 2>/dev/null [. for any letter, grep counts tabs and spaces as a character]
6. Use grep to find all files that contain the string "alex", but make sure that "alexander" is not included in the result
	1. echo 'alex' > /tmp/names.txt
	2. echo 'alexander' >> /tmp/names.txt
	3. grep alex /tmp/names.txt [this works if you are wanting the letters and don't mind part matches to words]
	4. grep '^alex$' /tmp/names.txt [this works if the word is the line but won't pick the word out of the line]
	5. echo 'alex is a polite person' >> /tmp/names.txt
	6. grep '\<alex\>' /tmp/names.txt [this looks for the word as a whole, there for doesn't match to part words]

- find the word or string in the contents of a file 'special'
	- grep -rnw 'special' /etc