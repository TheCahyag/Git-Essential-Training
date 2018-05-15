# Git Notes
### Written by Brandon Bires-Navel, using [Lynda](http://www.lynda.com)'s [Git Essential Training](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html?srchtrk=index:1%0Alinktypeid:2%0Aq:GIT%0Apage:1%0As:relevance%0Asa:true%0Aproducttypeid:2) tutorial

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
* List all current configurations set: git config --list
* Set name: git config --global user.name "Brandon Bires-Navel"
* Set email: git config --global user.email "brandonnavel@outlook.com"
* Tell Git what text editor you want to use: git config --global core.editor "vim"
* Tell Git to use colors when printing to the command line: git config --global color.ui true

### Git Commands

* `git help`: List a bunch of helpful and most used commands
    * `git help log`: Pulls up the Git Manual for the `log` command
* `git init`: Initialise a git repository
* `git add .`: Add all the files in the current directory to the git repo
* `git commit`: Commit the change
    * `git commit -m "Message"`: Commit with a message
    * `git commit -a`: Add all modified messages to the staging index and commit them
    * `git commit --amend`: Add changes that are in stage to the last commit
* `git log`: Show a log of all the commits made
    * `git log -n #`: Will return the last # commits from the log
    * `git log --since=2018-05-15`: Returns all commits since a specific date
    * `git log --until=2018-05015`: Returns all commits up to a specific date
    * `git log --author="Kevin"`: Returns all commits from Kevin
    * `git log --grep="bugs"`: Returns all the commits that has the string 'bugs' in the commit message
    * `git log HEAD`: Returns all the commits starting from the HEAD of the current branch
* `git status`: Reports to us the difference between the working directory, the staging index, and the repository
* `git diff`: Compare two files between the working directory and the other directories
    * `git diff --staged`: Return the changes between the staging directory and the other directories
    * `git diff --color-words`: Returns the changes, but instead of using two lines for a change it will only show the part of the line that was changed
* `git rm FILE`: Delete FILE from git and the repo, the change is already added to staging index
* `git mv OLD_FILE NEW_FILE`: Rename OLD_FILE to NEW_FILE and will add it to the staging index  
* `git checkout -- FILE`: Get the repo's version of FILE in the current branch (--) and replace the working directories version
* `git reset HEAD FILE`: Reset FILE to the version of the file that is in the HEAD commit


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
























