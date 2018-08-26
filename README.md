# Git Commands Cheatsheet
Quick reference/tricks in Git Commands

# Coverage

  - Git Help
  - Configuration
  - Starting Repository and Staging
  - Git Diff

## Git Help
General
```sh
$ git help
```
Specific
```sh
$ git help config
```
More Info: [Git Help]
## Git Configuration
Configuration command option list
```sh
$ git config
```
Note:
Single repo
```sh
--local //single repo
```
For your user
```sh
--global
```
All users and collaborators
```sh
--system
```
Basic setup
```sh
$ git config --global user.name "A Debugs Life"
$ git config --global user.email sample@adebugslife.com
```
### Viewing Global Configurations
```sh
$ git config --global --list
$ cat ~/.gitconfig
```
### Viewing Local Configurations
```sh
$ git config --local --list
$ cat .git/config
```
### Configuring Line Endings
Linux/Mac:
```sh
$ git config --global core.autocrlf input
$ git config --global core.autocrlf true
```
Window
```sh
$ git config --global core.autocrlf true
```
### Configuring Push Default
```sh
$ git config --global push.default simple
```
### Configuring Pull Default
```sh
$ git config --global pull.rebase true
```
### Reuse Recorded Resolution (ReReRe)
```sh
$ git config --global rerere.enabled true
```
### Configuring Output Colors
```sh
$ git config --global color.ui true
```
### Configuring Aliases
Beautify log configuration
```sh
git config --global alias.prettylog \ "log --pretty=format: '%h %s [%an]' --graph"
git config --global alias.mylogs \ "log --graph --decorate --pretty=oneline --abbrev-commit --all" 
```
Alias log - Refer to the set up above
```sh
git prettylog
git mylogs
```
Silent - Less space
```sh
$ git s
```
Sample:
git status to silent
```sh
$ git config --global alias.s "status -s"
$ git status -s
```
More Info: 
* [Git Configuration]
* [Git Alias]

## Starting Repository and Staging
Start the repo
```sh
$ git init
```
Check what's changed since last commit
```sh
$ git status
```
Add file to staging area
```sh
$ git add sample.txt
```
Add multiple specific files
```sh
git add sample1.txt sample2.txt
```
Add all newly added, modified, deleted files to staging
```sh
$ git add --all
```
Short hand of `git add --all`
```sh
$ git add .
```
Add all files with .txt extension. Note: you can put also any file extention after *.
```sh
$ git add *.txt
```
Add all .txt extension inside this specific directory
```sh
$ git add directoryName/*.txt
```
Add all files in this directory
```sh
$ git add directoryName/
```
Add all txt file in the whole project
```sh
$ git add "*.txt"
```

## Git Log
### Coloring and Simplify Log
Colorize log configuration
```sh
$ git config --global color.ui true
```
Commit logs with full SHA, Author, Long Date, Commit message
```sh
$ git log
```
Pretty oneline log
```sh
$ git log --pretty=oneline
```
Pretty format
```sh
$ git log --pretty=format: "&h %ad- %s [%an]"
```
Launch  Git log manual in the browser
```sh
$ git help log
```
Patch output
```sh
$ git log --oneline -p
```
Show how many insertion and deletion made
```sh
$ git log --oneline --stat
```
Show oneline of logs with branch graph
```sh
$ git log --oneline --graph
```

### Date Ranges
```sh
$ git log --until=1.minute.ago
$ git log --since=1.day.ago
$ git log --since=1.hour.ago
```
More Info: [Git Log]
## Git Diff
```sh
$ git diff
```
Same with git diff
```sh
$ git diff HEAD
```
Commit before the latest commit
```sh
$ git diff HEAD^
```
Previous 2 commits before the latest
```sh
$ git diff HEAD^^
```
5 previous commit from the latest
```sh
$ git diff HEAD~5 
```
Diff between 2 different commit with specific <SHA>
```sh
$ git diff <SHA> <SHA>
```
Diff between 2 branch
```sh
$ git diff master <branch>
```
View staged differences
```sh
$ git diff --staged
```
More info: [Git Diff]

   [Git Log]: <https://git-scm.com/docs/git-log>
   [Git Alias]: <https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases>
   [Git Configuration]: <https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration>
   [Git Help]: <https://git-scm.com/docs/git-help>
   [Git Diff]: <https://git-scm.com/docs/git-diff>
#### Reference

See [GIT](http://git-scm.com)


## Authors

* **Ann G.** - *Initial work* - [Adebugslife](http://adebugslife.com)


## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE.md](LICENSE.md) file for details