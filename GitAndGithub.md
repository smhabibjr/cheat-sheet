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
````
git reset --soft HEAD^      //Will keep the modified changes in your working tree.
````
````
git reset --hard HEAD^    //WILL THROW AWAY THE CHANGES YOU MADE !!!
````
Delete all branches except master command
To delete all branches in your Git repository except master, simply issue the following command:

````
git branch | grep -v "master" | xargs git branch -D
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

```sh
git push origin --all
```

## git conflicts.
Merge Request:

In a GitLab merge request or pull, "Use yours" and "Use theirs" appear when resolving merge conflicts. Their meanings are as follows:

"Use yours" → Keeps your changes (the changes from your branch).
"Use theirs" → Uses the changes from the target branch (the branch you are merging into).
For example, if you're merging feature-branch into main and there's a conflict:

#### Merge Request: from feature-branch to main-branch

Clicking "Use yours" keeps the conflicting lines from feature-branch.

#### Pull from main-branch to feature-branch

Clicking "Use theirs" keeps the conflicting lines from main.

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
