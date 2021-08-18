## Git Notes

* Git is a distributed version control system. A remote repository is present and everyone working will have there own version of repository.
* Changes are first made locally and pushed to remote repository
* By default a master branch is present. We can directly change that and push it if we have access.
* If multiple people working on a project. Branches can be created and pushed. Pushed branch can be merged with Master if no conflicts.
* Multiple people work on opensource project by forking a repository and updating and keeping a pull request.
* Existing project on local or remote repository can be tracked using git
* There are three states while working with git
  * Working directory - Directory which we are working in (all files will be present here)
  * Staging area - this is place where we organize files that we want to commit
     * We use staging area to commit files individually or in small chunks instead of commting at a time. This will allow us to be more detailed
  * Commited files


### Git commands

#### commands to use after installation of git
* git --version - checks the version of the installed locally git
* git config --global user.name "Name" - sets up the name of the user 
* git config --global user.email "yourname@somemail.com" - sets up the mail of the user

#### help commands
* git help <verb> # for getting documentation
* git <verb> --help # for getting documentation

#### intitiazation and removal of repository  
* git init - creates a .git directory which tracks all the changes in the folder
* rm -rf .git - removes the .git repository and all tracking is removed 
  
#### ignore and status
* touch .gitignore - creates a git ignore file
* git status - check working tree - both on the git and on local 
  
#### adding and removing files from staging area
* git add -A # adds all untracked files and files that we made changes to staging area
* git add <file name> # adds only this file to staging area
* using git status we can look at which files are in staging are
* git reset <file_name> - removes file from staging area
* git reset - removes all files from staging area
  
#### commiting changes
* git commit -m "Message to commit"
* git log - shows all the commits made, authors, dates as well
  
#### clonning a repository
* git clone <url> <localpath> - clone a repository
* git clone <url> . - clones to present folder

#### info of a repository
* git remote -v - lists the information about repositries
* git branch -a - lists all of the btanches in the remote and our repository

#### pushing to remote repository
* git diff - shows changes made to code
* First we need to commit changes to local repository  
* git pull origin master - pull the repository to local
* git push origin master - push the chages to remote
* It is good practice to pull the repository to get the latest before pushing
* origin is the remote repository name and master is the branch which we are pushing to
