`xFusionCorp Industries` has planned to set up a common email server in `Stork DC`. After several meetings and recommendations they have decided to use `postfix` as their `mail transfer agent` and `dovecot` as an `IMAP/POP3` server. We would like you to perform the following steps:
1.  Install and configure `postfix` on `Stork DC` mail server.    
2.  Create an email account `kirsty@stratos.xfusioncorp.com` identified by `ksH85UJjhb`.    
3.  Set its mail directory to `/home/kirsty/Maildir`.    
4.  Install and configure `dovecot` on the same server.

stmail01
172.16.238.17
stmail01.stratos.xfusioncorp.com
groot
Gr00T123
Nautilus Mail Server

%% ssh mail server stmail01 %% Gr00T123
ssh groot@stmail01
sudo -i

yum install postfix -y
yum install dovecot -y
yum install net-tools -y

%% configure postfix %%
find /etc -type f | grep postfix
vi /etc/postfix/main.cf
	under INTERNET HOST AND DOMAIN NAMES:
		myhostname = stmail01.stratos.xfusioncorp.com [decomment the line that has virtual.domain.tld and change it to this]
		mydomain = stratos.xfusioncorp.com [uncomment this line a few below the one above and change this from domain.tld]
	under SENDING MAIL
		myorigin = $mydomain
	under RECEIVING MAIL 
		inet_interfaces = all [uncomment this line]
		# inet_interfaces = localhost [comment out this line]
	right above rejecting main for unknown local users
		comment out the 1st mydestination line;
		mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain [uncomment this 2nd line]
	above INTERNET OR INTRANET
		mynetworks = 172.16.238.0/24, 127.0.0.0/8 [uncomment the top line and change the cidr]
	under DELIVERY TO MAILBOX
		home_mailbox = Maildir/ [uncomment this line]

systemctl start postfix
systemctl status postfix

%% add user as per request %% ksH85UJjhb
useradd kirsty
passwd kirsty

%% test postfix %%
telnet stmail01 25
EHLO localhost
mail from: kirsty@stratos.xfusioncorp.com
rcpt to:kirsty@stratos.xfusioncorp.com
DATA
test mail
.
quit
ls /home/kirsty/Maildir/new/
cat /home/kirsty/Maildir/new/[press 'tab' key to bring up a file in the new directory to confirm correct configuration]

%% configure dovecot %%
find /etc -type f -name | grep dovecot
vi /etc/dovecot/dovecot.conf
	protocols = imap pop3 lmtp [uncomment this line]
vi /etc/dovecot/conf.d/10-mail.conf
	mail_location = maildir:~/Maildir
vi /etc/dovecot/conf.d/10-auth.conf
	disable_plaintext_auth = yes [uncomment this line]
	auth_mechanisms = plain login [add 'login' to this line]
vi /etc/dovecot/conf.d/10-master.conf
	user = postfix
	group = postfix [uncomment both these lines and add postfix onto the end]

systemctl enable dovecot
systemctl start dovecot
systemctl status dovecot

%% test dovecot conf %%
telnet stmail01 110
user kirsty
pass [password]
test mail
quit
netstat -lnp | grep dovecot


I had issues authenticating kirsty & her password I tried multiple times and each time it failed, I even went back and reset her password thinking I messed it up.  In the end I just moved on and the activity still marked as successful.