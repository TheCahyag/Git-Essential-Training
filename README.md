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

