The backup server in the `Stratos DC` contains several template XML files used by the Nautilus application. However, these template XML files must be populated with valid data before they can be used. One of the daily tasks of a system admin working in the xFusionCorp industries is to apply string and file manipulation commands!
Replace all occurances of the string `Random` to `Marine` on the XML file `/root/nautilus.xml` located in the backup server.

stbkp01
172.16.238.16
stbkp01.stratos.xfusioncorp.com
clint
H@wk3y3
Nautilus Backup Server

--ssh into stbkp01:
ssh clint@172.16.238.16 -i .ssh/authorized_keys
H@wk3y3  %%type password%% 
pwd
sudo cat /root/nautilus.xml
sudo -i
cat /root/nautilus.xml | grep Random | wc -l %%66%%
cat /root/nautilus.xml | grep Marine | wc -l  %%0%%
sed -i 's/Random/Marine/g' /root/nautilus.xml 
cat /root/nautilus.xml | grep Random | wc -l %%0%%
cat /root/nautilus.xml | grep Marine | wc -l  %%66%%

