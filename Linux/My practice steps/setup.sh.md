#!/bin/bash

sudo apt update
sudo apt upgrade -y
groupadd developer
groupadd admin
useradd -g developer Bob
mkdir -p /usr/local/networking
touch /usr/local/networking/routing.txt

sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
sudo apt install apache2 -y
sudo apt install docker.io -y
mkdir -p /usr/local/links/
touch /usr/local/links/hardlinkme.txt
touch /usr/local/links/softlinkme.txt
mkdir -p /usr/local/links/hardlinks/
touch /usr/local/links/hardlinks/linknum
touch /file{1..5}.txt
tar -cvf /opt/SAMPLE001.zip /file1.txt /file2.txt /file3.txt
docker container create --name docker1 -p 81:8081 nginx
docker container create --name docker2 -p 82:8082 nginx
docker container start docker1
docker container start docker2
echo '-----BEGIN RSA PRIVATE KEY-----

-----END RSA PRIVATE KEY-----' > /root/RemoteLinuxKey.pem
chmod 0400 /root/RemoteLinuxKey.pem
mkdir -p /usr/backups
mkdir -p /usr/archive
mkdir -p /srv/dns/
touch /srv/dns/dnsservice
touch /srv/dns/dns-service

mkdir /raid
touch /usr/raid-config
mkdir /mnt/backup

groupadd contractors
groupadd employees

mkdir -p /home/example
touch /home/example/file1
touch /home/example/file2
touch /home/example/file3
touch /home/example/file4
touch /home/example/file5
touch /home/example/file6
touch /home/example/file7
touch /home/example/file8
touch /home/example/file9
touch /home/example/file0

useradd Sue
chown Sue:admin /home/example/file*
chown Bob:admin /home/example/file0
chmod 2000 /home/example/file8
chmod 2000 /home/example/file6
fallocate -l 126M /home/example/file10
fallocate -l 512k /home/example/file11
useradd -m -d /tmp/projectadmin projectadmin 
useradd devel
apt install zsh -y
chsh -s $(which zsh) devel

mkdir -p /home/student/textreferences/

for i in {1..6999}; do echo "This is our Earth" >> /home/student/textreferences/editme.txt; done;
echo "this line will be removed" >> /home/student/textreferences/editme.txt # this is line 7000
for i in {1..776}; do echo "This is our earth" >> /home/student/textreferences/editme.txt; done;
echo "this will be carried to the beginning" >> /home/student/textreferences/editme.txt # this is line 7777

mkdir -p /usr/script/
touch /usr/script/file
touch /usr/script/sampleone.txt
touch /usr/script/samplescript.sh
chmod 777 /usr/script/samplescript.sh
touch /usr/script/file
touch /usr/script/sampletwo.txt
touch /usr/script/samplescript2.sh
chmod 777 /usr/script/samplescript2.sh
touch /usr/script/samplethree.txt
echo -e '#!/bin/bash \n /usr/bin/ls /usr/script/file /usr/script/not-a-file'  > /usr/script/samplescript.sh
echo -e '#!/bin/bash \n /usr/bin/ls /usr/script/file /usr/script/not-a-file'  > /usr/script/samplescript2.sh

mkdir -p /srv/SAMPLE002
touch /srv/SAMPLE002/file1
touch /srv/SAMPLE002/file2
touch /srv/SAMPLE002/file3
touch /srv/SAMPLE002/file4
touch -t 8001031305 /srv/SAMPLE002/file5
touch -t 8001031305 /srv/SAMPLE002/file6
touch /srv/SAMPLE002/file7
mkdir -p /srv/SAMPLE002/dir1
mkdir -p /srv/SAMPLE002/dir2
mkdir -p /srv/SAMPLE002/dir3
touch /srv/SAMPLE002/file1.tar
touch /srv/SAMPLE002/file2.tar
chmod 777 /srv/SAMPLE002/file1
chmod 777 /srv/SAMPLE002/file2
mkdir -p /opt/SAMPLE002
echo 'this has already been created for an exercise, this line should be removed in successful completion of said exercise' > /opt/SAMPLE002/toBeCrompressed.txt

mkdir -p /usr/sample/
touch /usr/sample/example.txt

mkdir -p /staging

echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
echo "Linux is cool" >> /usr/sample/example.txt
echo "It is cool to know Linux" >> /usr/sample/example.txt
echo "Wow this line has Linux in the middle" >> /usr/sample/example.txt
echo "Wow this line has Linux and yay" >> /usr/sample/example.txt
echo "This is the last line yay" >> /usr/sample/example.txt
cp /usr/sample/example.txt /srv/SAMPLE002/example.txt
cp /usr/sample/example.txt /srv/SAMPLE002/example1.txt
cp /usr/sample/example.txt /srv/SAMPLE002/example2.txt

mkdir -p /usr/diff/
touch /usr/diff/file1
touch /usr/diff/file2
touch /usr/diff/file3
touch /usr/diff/file4
touch /usr/diff/file5
echo "yay" > /usr/diff/file1
echo "yay" > /usr/diff/file2
echo "yay" > /usr/diff/file3
echo "yay" > /usr/diff/file5
echo "oh no" > /usr/diff/file4

mkdir -p /usr/diff/diff1
mkdir -p /usr/diff/diff2
touch /usr/diff/diff1/file1
touch /usr/diff/diff1/file2
touch /usr/diff/diff1/file3
touch /usr/diff/diff2/file1
touch /usr/diff/diff2/file2
touch /usr/diff/diff2/file3
touch /usr/diff/diff1/file9
touch /usr/diff/diff2/file0
echo "oh no" > /usr/diff/diff1/file9
echo "yay" > /usr/diff/diff2/file0

mkdir -p /usr/acl
touch /usr/acl/file.txt
touch /home/delete.me
chattr +i /home/delete.me

touch /home/example/answer1
touch /home/example/answer2
touch /home/example/answer3
touch /home/example/answer4
touch /home/example/answer5