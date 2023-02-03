Go to Isengard.
Click the copy symbol next to 'Admin' on your account
a pop up box will appear
Click on the down arrow next to powershell, then click 'Copy Powershell'
In VSCode, open terminal and paste copied command.  press enter.
to confirm setup type in CLI:
aws s3 ls %%This should output a list of all s3 buckets on your  account%%






%%configure git to github%%
git config user.name "username"
git config user.email "user@email.com" 

%%commands to push to github%%
git add [filename]
git commit -ms "commit name or reason"
git push -u origin

%%setuplocalproject%% 
mkdir git-[projectname]
cd git-[projectname]
git init
ls -l .git

%%others%% 
git diff - shows the difference of files add and then changed;
git log
git clone
git init 
git gui or git-gui
git k 
cgit - can be installed in concert with a web server to enable very efficient repository browsing
gitweb
git --version
git help [command]
git help --all


![[Pasted image 20230127115936.png]]