````sh 
git init
````
git init is use to initialize local repository in a folder.

````sh 
git status
````
git status is use to check the stautus of your working directory like which files are modified or
changed.

````sh 
git status -s
````
shorthand use to check status when if we have too much files ,First M shows that file is modified
in staging area and secound M shows that file is modified in working tree.

````sh
git add .
````
git add . is use to add all files in the wolder to the repository.

````sh
git add -A
````
git add -A is also use to add all files and folder to the repository.

````sh
git commit -a "your commit"
````
commit is use to commit changes in git at a point.

````sh
git commit -a -m "your commit"
````
git commit -a -m "your commit" is use to skip stagging area and directly commit a changes.

````sh
git checkout 'your file name'
````
git checkout is use to match the input file with the last commit.

````sh
git checkout -f
````
git checkout -f is use to match all files of the directory to the last commit.

````sh 
git log
````
git log is use to check the commits of the project.

````sh
git log -p -<number>
````
git log with a -[number] is use to see last commits in range of the number.

````sh
git diff
````
git diff is use to check diffrent between working tree and the staging area.

````sh
git diff --staged
````
git diff --staged is use to check the diffrence between stage area and the last commit.

````sh
touch "file name"
````
touch command is use to create a files.

````sh
git rm "file name"
````
git rm is use to remove a file from working directory and staging area.

````sh
git rm --chached "file name"
````
git rm --chached "filename" is use to remove file from staging area and exist in working
directory.

````sh
git branch
````
git branch is use to check the avilable branch or check the active branch.

````sh
git branch "branch name"
````
git branch is use to create a new branch.

````sh
git checkout "branch name"
````
git checkout "branch name" is use to swich the git branch.

````sh
git merg "branch name"
````
git merg "branch name" is use to merg other branch with your current branch.

````sh
git checkout -b "branch name"
````
git checkout -b "branch name" create a new branch and switch into it.

## Deploy on github.

````sh
git remote add origin https://github.com/username/repositoryname.git
````
Is use to connect remote repository to our local repository.

````sh
git remote
````
return the remote.

````sh
git remote -v
````
return the urls of remote where we fetch or push.

````sh
git remote set-url orgin https://github.com/username/repositoryname.git
````
change/update your remote url.

````sh
git push -u orgin "branch name"
````
we are telling to github where we pushing next time we only need to write ($git push)
it also push our code to the same place but first time we must tell it.	

````sh
git push origin "branch name"
````
git push is use to push our code/files to our remote(origin) and on which branch it push.
	
## Creating .ssh key and add into gihub account.
### Genrating a new ssh key.

````sh
ssh-keygen -t ed25519 -C "your_email@example.com"
````

paraphase (just click enter)

````sh
eval "$(ssh-agent -s)"
````
agent key process id.

### Adding ssh key to github.

````sh
ssh-add ~/.ssh/id_ed25519
````

````sh
clip < ~/.ssh/id_ed25519.pub
````
Copies the contents of the id_ed25519.pub file to your clipboard.

Then go to the github settings/SSH and GPG keys/(click on)new ssh key
in title type your title and in key paste your key.

### Git Remote 
````bsh
git remote -v
````

## .gitignore
.gitignore is a file that can be only creating using ($touch .gitignore) command , In git
ignore we write directly file name and git ignore it from monitoring it , /"file name" is use
to ignore file in where there is gitignore and it cannot ignore the file in any folder,and *.ext
is use to ignore all types of files where there the file extension is .ext , for ignoring a
folder in gitignore after folder name use '/'.
