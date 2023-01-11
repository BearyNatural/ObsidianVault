There is some data on `Nautilus App Server 1` in `Stratos DC`. Data needs to be altered in several of the files. On `Nautilus App Server 1`, alter the `/home/BSD.txt` file as per details given below:

a. Delete all lines containing word `software` and save results in `/home/BSD_DELETE.txt` file. (Please be aware of case sensitivity)

b. Replace all occurrence of word `and` to `for` and save results in `/home/BSD_REPLACE.txt` file.

`Note:` Let's say you are asked to replace word `to` with `from`. In that case, make sure not to alter any words containing this string; for example up`to`, contribu`to`r etc.

stapp01
172.16.238.10
stapp01.stratos.xfusioncorp.com
tony
Ir0nM@n
Nautilus App 1

--ssh into stapp01:
ssh tony@172.16.238.10 -i .ssh/authorized_keys
Ir0nM@n   %%type password%% 
pwd
sudo -i
pwd
cat /home/BSD.txt

a:
ll /home
cat /home/BSD.txt | grep software | wc -l %%18%%
cp /home/BSD.txt /home/BSD_DELETE.txt 
ll /home
cat /home/BSD_DELETE.txt | grep software | wc -l %%18%%
gawk -i inplace '!/software/' /home/BSD_DELETE.txt
cat /home/BSD_DELETE.txt | grep software | wc -l %%18%% [the gawk command did not work]
sed -i '/software/d' /home/BSD_DELETE.txt
cat /home/BSD_DELETE.txt | grep software | wc -l %%0%%
grep software /home/BSD.txt
grep software /home/BSD_DELETE.txt

b:
cat /home/BSD.txt | grep and | wc -l %%24%%
cat /home/BSD.txt | grep for | wc -l %%12%%
cp /home/BSD.txt /home/BSD_REPLACE.txt 
ll /home
cat /home/BSD_REPLACE.txt | grep and | wc -l %%24%%
cat /home/BSD_REPLACE.txt | grep for | wc -l %%12%%
sed -i 's/and/for/g' /home/BSD_REPLACE.txt 
cat /home/BSD_REPLACE.txt | grep and | wc -l %%0%%
cat /home/BSD_REPLACE.txt | grep for | wc -l %%30%%
grep and /home/BSD.txt
grep for /home/BSD_REPLACE.txt

%%
-- different ways of doing the above:
grep -v "software" /home/BSD.txt > /home/BSD_DELETE.txt [can also use the following commands:]
awk '!/software/' /home/BSD.txt > /home/BSD_DELETE.txt
or
gawk -i inplace '!/software/' /home/BSD_DELETE.txt [this will save over the original file so cp it first to the new file]
sed -i '/software/d' /home/BSD_DELETE.txt [the -i allows editing files in-place.  The -i option takes an optional extension arguement in case we want to save the original file as a backup with that extension.if no extension is given, the backup will be skipped:]
%%

