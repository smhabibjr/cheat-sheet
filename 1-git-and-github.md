````sh 
git init
````
````sh 
git status
````
````sh 
git status -s
````
````sh
git add .
````
````sh
git add -A
````
````sh
git commit -a "your commit"
````
````sh
git commit -a -m "your commit"
````
````sh
git checkout 'your file name'
````
````sh
git checkout -f
````
````sh 
git log
````
````sh
git log -p -<number>
````
````sh
git diff
````
````sh
git diff --staged
````
````sh
touch "file name"
````
````sh
git rm "file name"
````
````sh
git rm --chached "file name"
````
````sh
git branch
````
````sh
git branch "branch name"
````
````sh
git checkout "branch name"
````
````sh
git merg "branch name"
````
````sh
git checkout -b "branch name"
````
## Deploy on github.

````sh
git remote add origin https://github.com/username/repositoryname.git
````
````sh
git remote
````
````sh
git remote -v
````
````sh
git remote rm origin
````
````sh
git remote set-url orgin https://github.com/username/repositoryname.git
````
````sh
git push -u orgin "branch name"
````
````sh
git push origin "branch name"
````
	
## Creating .ssh key and add into gihub account.
### Genrating a new ssh key.

````sh
ssh-keygen -t ed25519 -C "your_email@example.com"
````
````sh
eval "$(ssh-agent -s)"
````

### Adding ssh key to github.

````sh
ssh-add ~/.ssh/id_ed25519
````
````sh
clip < ~/.ssh/id_ed25519.pub

## .gitignore
.gitignore is a file that can be only creating using ($touch .gitignore) command , In git
ignore we write directly file name and git ignore it from monitoring it , /"file name" is use
to ignore file in where there is gitignore and it cannot ignore the file in any folder,and *.ext
is use to ignore all types of files where there the file extension is .ext , for ignoring a
folder in gitignore after folder name use '/'.
