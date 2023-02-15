As per new application requirements shared by the `Nautilus` project development team, serveral new packages need to be installed on all app servers in `Stratos Datacenter`. Most of them are completed except for `epel-release`.

Therefore, install the `epel-release` package on all `app-servers`.

%% ssh into stapp01 %% Ir0nM@n
ssh tony@stapp01
sudo yum install epel-release -y
exit

%% ssh into stapp02 %% Am3ric@
ssh steve@stapp02
sudo yum install epel-release -y
exit

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
sudo yum install epel-release -y
exit
