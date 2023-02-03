git init <respository/projectName> [this initializes existing git repository in the folder you are in]


git add <fileName> [this adds a file to the list for pushing/commiting to github]
git commit -m "test commit" [commits the files added to a push]
git push -u origin <main> [pushes the files to github]

echo 'some junk' > somejunkfilename
echo another line >> somejunkfilename
git diff
git log

git commit -s -m "My initial commit" [**Signed-off-by** line to the commit with the **-s** option]

git checkout master #change the local name
git branch -m master main

#change the remote name
git push -u origin main

#confirm the names
git branch -a

%% Depending on th setup of the remote server, this may or may not work.  An easier approach is to not delete the master branch bu just copy it to main and work from there from now on, as in: %%
git checkout master
git branch main
git checkout main
git push -u origin main
# and then just ignore master from now on.