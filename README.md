# Git Notes
#### Written by Brandon Bires-Navel, using [Lynda](http://www.lynda.com)'s [Git Essential Training](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html?srchtrk=index:1%0Alinktypeid:2%0Aq:GIT%0Apage:1%0As:relevance%0Asa:true%0Aproducttypeid:2) tutorial

## TOC
TODO  
  
## Git
Git is a distributed version control, open source, free software, compatible with most platforms, very fast, and has safeguards set in place to protect against data corruption. Git was born in April of 2005, created by Linus Torvalds to manage Linux kernel source code.  
  
### Distributed Version Control
Different uses maintain their own repositories, instead of working from a central repository. Changes are stored as "change sets" or "patches". Git tracks changes, not versions.  
  
No single master repository; just many working copies, each with their own combination of change sets.  
  
### Basic Configuration

#### System
Located at /etc/gitconfig  
git config --system  

#### User
Located at ~/.gitconfig  
git config --global  

#### Project
Located at my_project/.git/config  
git config  

#### Modifying Configs
* `git config --list`: List all current configurations set
* `git config --global user.name "Brandon Bires-Navel"`: Set name
* `git config --global user.email "brandonnavel@outlook.com"`: Set email
* `git config --global core.editor "vim"`: Tell Git what text editor you want to use
* `git config --global color.ui true`: Tell Git to use colors when printing to the command line

### Git Commands

* `git help`: List a bunch of helpful and most used commands
    * `git help log`: Pulls up the Git Manual for the `log` command
* `git init`: Initialize a git repository
* `git add .`: Add all the files in the current directory to the git repo
* `git commit`: Commit the change
    * `git commit -m "Message"`: Commit with a message
    * `git commit -a`: Add all modified messages to the staging index and commit them
    * `git commit --amend`: Add changes that are in stage to the last commit
* `git log`: Show a log of all the commits made
    * `git log -n #`: Will return the last # commits from the log
    * `git log --since=2018-05-15`: Returns all commits since a specific date
    * `git log --until=2018-05-15`: Returns all commits up to a specific date
    * `git log --author="Kevin"`: Returns all commits from Kevin
    * `git log --grep="bugs"`: Returns all the commits that has the string 'bugs' in the commit message
    * `git log HEAD`: Returns all the commits starting from the HEAD of the current branch
    * `git log --oneline`: Returns the log where each commit only takes up one line
    * `git log --oneline -4`: Returns the last 4 entries of the log where each commit only takes up one line
    * `git log c4bd56.. index.html`: Returns all commits that are related to index.html
    * `git log --graph --oneline --decorate --all`: Get changes from all branches as one line commits
* `git status`: Reports to us the difference between the working directory, the staging index, and the repository
* `git diff`: Compare two files between the working directory and the other directories
    * `git diff --staged`: Return the changes between the staging directory and the other directories
    * `git diff --color-words`: Returns the changes, but instead of using two lines for a change it will only show the part of the line that was changed
    * `git diff SHA-1`: Returns the differences between the working directory and the commit specified
    * `git diff SHA-1..SHA-1`: Returns the differences between two different the repo in two different commits
    * `git diff --stat --summary SHA-1..SHA-1`: Show a summary of changes between two versions of the repo and give some statistics on the changes
    * `git diff master..other_branch`: Shows the differences between the tip of master and the tip of other_branch
* `git rm FILE`: Delete FILE from git and the repo, the change is already added to staging index
* `git mv OLD_FILE NEW_FILE`: Rename OLD_FILE to NEW_FILE and will add it to the staging index  
* `git checkout -- FILE`: Get the repo's version of FILE in the current branch (--) and replace the working directories version
* `git reset HEAD FILE`: Reset FILE to the version of the file that is in the HEAD commit
* `git show SHA-1`: Show the changes made in a specific commit
* `git branch`: Show all the branches that are on the local machine
    * `git branch NEW_BRANCH`: Create branch NEW_BRANCH
    * `git branch --merged`: Shows all the branches that are completely included in the current branch
    * `git branch -m OLD_BRANCH NEW_BRANCH`: Rename OLD_BRANCH to NEW_BRANCH
    * `git branch -d BRANCH_NAME`: Delete branch BRANCH_NAME, given there are no unmerged commits
* `git checkout BRANCH`: Switch to the BRANCH branch
    * `git checkout -b NEW_BRANCH`: Create a new branch and switch to it
* `git merge BRANCH`: Merge BRANCH into the current branch
    * `git merge --ff-only BRANCH`: Only merge BRANCH into the current directory if a fast-forward merge can be done, otherwise abort
    * `git merge --abort`: Abort the current merge
* `git stash save "message for stash"`: Stash changes to move to a different branch
    * `git stash list`: List all the stashes available 
* `git fetch origin`: Fetchs data from the origin remote repo

#### Git Commit Message Etiquette
* Keep the message a short single-line summary (less than 50 characters) orr
* Optionally followed by a blank line and a more complete description
* Bullet points are usually asterisks or hyphens
* You can add "ticket tracking numbers" from bugs or support requests
Example:  
Bad - "Fix typo"  
Good - "Added missing > in project section of HTML"

#### Git HEAD
A pointer to the "tip" of the current branch in the repo, at any given time there is only one HEAD  
  
#### Git Reset
git reset  
    --soft, does not change staging index or working directory  
    --mixed (default), changes staging index to match repository and does not change working directory  
    --hard, changes staging index and working directory to match repository  

#### Git Ignore Files
Some syntax may include:
* Normal regular expression stuff
    * `*.php`: Any file that ends in '.php'
    * `!index.php`: Even though all .php files are ignored, don't ignore index.php
* Trailing `/` will include all files in a folder
    * `assets/videos/` will ignore all files in the videos folder
* Comments are after `#`

##### Files you would likely want to ignore
* Compiled source code
* Packages and compressed files (.zip, .tar, .rar, .etc)
* Logs and databases
* Operating system generated files
* User-uploaded assets (images, PDFs, videos)

##### Global Git Ignore Files
`git config --global core.excludesfile ~/.gitignore_global`: Set the .gitignore file for the user rather than the repo  

#### Referencing Commits
* `HEAD^`: Find the parent commit of HEAD
* `HEAD~3`: Find the 3rd parent commit
* `git ls-tree HEAD`: List the files that are in the repo at the HEAD commit

#### Git Branches
Branches are cheap and all you to try new ideas without having to make a bunch of commits to master and subsequently reverting those changes if things don't work out.  

#### Git Merge

##### Merge Conflicts
If you merge two branches that conflict a new branch will be created named `branch|MERGING` in which you will need to go through the files that are conflicting (which can be seen with `git status`) or alternatively you can abort the merge by running `git merge --abort`.  
  
After you have resolved the conflicts, you need to add the changes with `git add file` and then `git commit` with no message. The branch will then continue with the merge.    
  
##### Tips to avoid conflicts
* Keep lines short
* Keep comments small and focused
* Beware stray edits to whitespace
    * spaces, tabs, line returns
* Merge often
* Track changes to master, while editing another branch always add the changes that are occurring in master using `git merge master` when in your other branch (this is called tracking)

#### Git Fetch
Fetching is not harmful at all  
* Fetch before you work
* Fetch before you push
* Fetch often
  
After you fetch you can decide what you want to do with the new data, be it merging or not doing anything  

#### Git Alias
`git config --global alias.co checkout`
`git config --global alias.ci commit`
`git config --global alias.br branch`
`git config --global alias.df diff`
`git config --global alias.dfs "diff --staged"`
`git config --global alias.logg "log --graph --decorate --oneline --abbrev-commit --all"`











