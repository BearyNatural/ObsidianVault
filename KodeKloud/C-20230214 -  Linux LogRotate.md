The `Nautilus` DevOps team is ready to launch a new application, which they will deploy on app servers in `Stratos Datacenter`. They are expecting significant traffic/usage of `haproxy` on app servers after that. This will generate massive logs, creating huge log files. To utilise the storage efficiently, they need to compress the log files and need to rotate old logs. Check the requirements shared below:

a. In all app servers install `haproxy` package.
b. Using `logrotate` configure `haproxy` logs rotation to monthly and keep only 3 rotated logs.
(If by default log rotation is set, then please update configuration as needed)

%% ssh into stapp01%% Ir0nM@n
ssh tony@stapp01
sudo yum install haproxy -y
find /etc | grep haproxy
cat /etc/logrotate.d/haproxy [weekly rotation; rotate 10]
sudo vi /etc/logrotate.d/haproxy %% change the following lines from: to [] %%
weekly [monthly]
rotate 4 [rotate 3]
cat /etc/logrotate.d/haproxy
systemctl status haproxy
sudo systemctl start haproxy
exit

%% ssh into stapp02 %% Am3ric@
ssh steve@stapp02
sudo yum install haproxy -y
sudo vi /etc/logrotate.d/haproxy %% change the following lines from: to [] %%
weekly [monthly]
rotate 4 [rotate 3]
cat /etc/logrotate.d/haproxy
systemctl status haproxy
sudo systemctl start haproxy
systemctl status haproxy
exit

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
sudo yum install haproxy -y
sudo vi /etc/logrotate.d/haproxy %% change the following lines from: to [] %%
weekly [monthly]
rotate 4 [rotate 3]
cat /etc/logrotate.d/haproxy
systemctl status haproxy
sudo systemctl start haproxy
systemctl status haproxy
exit
