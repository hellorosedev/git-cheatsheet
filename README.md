# Git Commands Cheatsheet
Quick reference/tricks in Git Commands

# Coverage

  - [Git Help](https://github.com/adebugslife/git-cheatsheet#git-help)
  - [Git Configuration](https://github.com/adebugslife/git-cheatsheet#git-configuration)
  - [Excluding Files](https://github.com/adebugslife/git-cheatsheet#excluding-files)
  - [Starting Repository and Staging (Local)](https://github.com/adebugslife/git-cheatsheet#starting-repository-and-staging-local)
  - [Remove Untracked File and Delete from File System](https://github.com/adebugslife/git-cheatsheet#remove-untracked-file-and-delete-from-file-system)
  - [Add to Staging](https://github.com/adebugslife/git-cheatsheet#add-to-staging)
  - [Commit](https://github.com/adebugslife/git-cheatsheet#commit)
  - [Remote](https://github.com/adebugslife/git-cheatsheet#remote)
  - [Git Log](https://github.com/adebugslife/git-cheatsheet#git-log)
  - [Git Diff](https://github.com/adebugslife/git-cheatsheet#git-diff)
  - [Blame](https://github.com/adebugslife/git-cheatsheet#blame)
  - [Branching Out](https://github.com/adebugslife/git-cheatsheet#branching-out)
  - [Collaboration](https://github.com/adebugslife/git-cheatsheet#collaboration)
  - [Tagging](https://github.com/adebugslife/git-cheatsheet#tagging)
  - [Rebase](https://github.com/adebugslife/git-cheatsheet#rebase)
  - [Interactive Rebase](https://github.com/adebugslife/git-cheatsheet#interactive-rebase)
  - [Purging History](https://github.com/adebugslife/git-cheatsheet#purging-history)
  - [Index Filter](https://github.com/adebugslife/git-cheatsheet#index-filter)
  - [Prune empty commits](https://github.com/adebugslife/git-cheatsheet#prune-empty-commits)
  - [Line Endings](https://github.com/adebugslife/git-cheatsheet#prune-empty-commits)
  - [Git attribute file](https://github.com/adebugslife/git-cheatsheet#git-attribute-file)
  - [Cherry-Pick](https://github.com/adebugslife/git-cheatsheet#git-attribute-file)
  - [Submodules](https://github.com/adebugslife/git-cheatsheet#submodules)
  - [Cloning Projects](https://github.com/adebugslife/git-cheatsheet#cloning-projects)
  - [Reflog](https://github.com/adebugslife/git-cheatsheet#reflog)
  


## Git Help

| Commands | Function |
| ------ | ------ |
| `$ git help` | General |
| `$ git help config` | Specific |

More Info: [Git Help]
## Git Configuration
Configuration command option list
```sh
$ git config
```
| Commands | Function |
| ------ | ------ |
| `--local` | Single repo |
| `--global` | For your user |
| `--system` | All users and collaborators |

### Basic setup
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
$ git config --global alias.prettylog \ "log --pretty=format: '%h %s [%an]' --graph"
$ git config --global alias.mylogs \ "log --graph --decorate --pretty=oneline --abbrev-commit --all" 
```
Alias log - Refer to the set up above
```sh
$ git prettylog
$ git mylogs
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

## Excluding Files
### For Local
Example: You don't want node_modules/ to be included in your folder in git. You also don't want it to display in "Untracked files"

Step:
1. Go to .git/info/exclude
2. Add the folder name: node_modules/
3. git status

### Exclude patterns
| Commands | Function |
| ------ | ------ |
| `file.txt` | Exclude specific file |
| `*.txt` | Exclude all .txt files |
| `dir_name/` | Exclude folder |
| `dir_name/*.txt` | Exclude all the txt files inside dir_name/ |

### For Both Local & Remote
use *.gitignore* and add exclude patterns (**IDEAL**)

## Starting Repository and Staging (Local)
Start the repo in local
```sh
$ git init
```
Check what's changed since last commit
```sh
$ git status
```
### Remove Untracked File and Delete from File System
| Commands | Function |
| ------ | ------ |
| `$ git clean -n` | Check status what would happen if you run `git clean` |
| `$ git clean -nd` | Check status what would happen if you run `git clean -fd` |
| `$ git clean -f` | Force removal from untracked file and delete it from file system |
| `$ git clean -fd` | Shorthand of `git clean -f -d`. Removal from untracked and delete the directory from file system |
| `$ git clean -d -f -f` | Git will refuse to delete directories with .git sub directory or file unless a second -f is given (e.g. submodule) |
| `$ git clean -fx` | Shorthand of `git clean -f -x`. Remove ignored files |
| `$ git clean -fX` | Shorthand of `git clean -f -X`. Remove ignored and non-ignored files |
| `$ git clean -fdx` | Remove ignored files and directory |
| `$ git clean -fdxn` | Check status what would happen if you run `git clean -fdx` |
| `$ git clean -f <file>` | Remove untracked files from particular subdirectory |
| `$ git clean -fxd <dir_path>` | Remove ignored and non-ignored untracked files/directory from particular subdirectory |
More Info: [Git Clean]

## Add to Staging
| Commands | Function |
| ------ | ------ |
| `$ git add sample.txt` | Add file to staging area |
| `$ git add sample1.txt sample2.txt` | Add multiple specific files |
| `$ git add --all` | Add all newly added, modified, deleted files to staging |
| `$ git add .` | Short hand of `git add --all` |
| `$ git add *.txt` | Add all files with .txt extension. Note: you can put also any file extention after *. |
| `$ git add directoryName/*.txt` | Add all .txt extension inside this specific directory |
| `$ git add directoryName/` | Add all files in this directory |

### Unstaged File
| Commands | Function |
| ------ | ------ |
| `$ git rm --cached file.txt` | Unstage file and add file in *.gitignore* to untrack the file forever without deleting it |
| `$ git reset HEAD file.txt` | *HEAD* refers to last commit in the current timeline and branch |
| `$ git checkout -- file.txt` | Restored to its previous state. Reset all modification in this file. Don't staged or untracked but excluded in *.gitignore* |

## Commit
| Commands | Function |
| ------ | ------ |
| `$ git commit -m "My first commit"` | Add file to staging area |
| `$ git commit -a -m "Modified file commit"` | Commit modified file ONLY. No need to stage |
| `$ git commit -am "Modified file commit"` | Shorthand for `$ git commit -a -m "Modified file commit"` |

### Undoing Commit
| Commands | Function |
| ------ | ------ |
| `$ git reset --soft HEAD^` | Remove from commit. Reset into staging. Move to commit before 'HEAD' |
| `$ git reset --hard HEAD^` | Undo last commit and all changes |
| `$ git reset --hard HEAD^^` | Undo  last 2 commits and all changes |

# Stash
| Commands | Function |
| ------ | ------ |
| `$ git stash` | Temporary save codes |
| `$ git stash save "Message"` | Temporary save - Codes and add custom message |
| `$ git stash save -u` | Temporary save - Untracked files |
| `git stash branch <NAME> stash@{NUMBER}` | Create new branch with latest stash |
| `$ git stash create` | Create an unreferenced commit, but it won't actually clear the local changes |
| `$ git stash show` | Summary of diffs |
| `$ git stash list` | List all stash |
| `$ git stash pop` | Retrieve latest stash and remove its record|
| `$ git stash apply stash@{NUMBER}` | Delete specific stash but retain its record |
| `$ git stash drop stash@{NUMBER}` | Delete specific stash |
| `$ git stash clear` | Delete all stash |

**Scenario: Need to commit changes but you are in the wrong branch**
1. `$ git stash save "Message"` to save changes even you are in the wrong branch
2. `$ git checkout BRANCHNAME`
3. `$ git stash pop` - to retrieved saved codes (It will delete the stash after retrieval)
4. `$ git commit -am "Message"`

## Remote
Note:
'add' = New remote
'origin' = Our name for this remote

| Commands | Function |
| ------ | ------ |
| `$ git remote -v` | Show remote repositories |
| `$ git remote add <name> <address>` | Add remote repo |
| `$ git push -u <name> <branch>` | Push local to remote repo|
| `$ git remote rm <name>` | Remove remotes |

### Change remote url
```sh
git remote set-url origin https://github.com/accountName/repoName.git
```

### Pushing to remote
```sh
$ git push -u origin master
```
Note:
`origin` = remote repository name
`master` = local branch to push

Password cache: https://help.github.com/articles/set-up-git
Use: Enter password once

### Pull from Remote
```sh
$ git pull
```
### Clone
```sh
$ git clone https://github.com/accountName/repoName.git
```

### Removing remote branch
```sh
$ git push origin :myfeature
$ git branch -d myfeature //FAILED: Must delete local branch manually
$ git branch -D myfeature //Force removal of remote branch
```
Scenario: What if Person 1 push to delete remote branch?
```sh
$ git commit -am "My commit to myfeature"
$ git push
$ git remote show origin //If the refs/remotes/origin is stale someones deleted it
$ git remote prune origin //Remove stale branches
```


### Git Remote
**Create a new repository on the command line**
```sh
$ echo "# test" >> README.md
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git remote add origin https://github.com/adebugslife/test.git
$ git push -u origin master
```
**Push an existing repository from the command line**
```sh
$ git remote add origin https://github.com/adebugslife/test.git
$ git push -u origin master
```
### Heroku Remote
```sh
$ heroku create
$ git remote -v
$ git push heroku master
```
### Remote push branch to Heroku
```sh
$ git branch
$ git push heroku-staging staging //FAILED: only master branch will be deploy to Heroku
$ git push heroku-staging staging:master //Will push your branch to Heroku master branch
```

## Git Log
### Coloring and Simplify Log
Colorize log configuration
```sh
$ git config --global color.ui true
```
| Commands | Function |
| ------ | ------ |
| `$ git log` | Commit logs with full SHA, Author, Long Date, Commit message |
| `$ git log --pretty=oneline` | Pretty oneline log |
| `$ git log --pretty=format: "&h %ad- %s [%an]"` | Pretty format |
| `$ git help log` | Launch  Git log manual in the browser |
| `$ git log --oneline -p` | Patch output |
| `$ git log --oneline --stat` | Show how many insertion and deletion made |
| `$ git log --oneline --graph` | Show oneline of logs with branch graph |

### Date Ranges
```sh
$ git log --until=1.minute.ago
$ git log --since=1.day.ago
$ git log --since=1.hour.ago
```
More Info: [Git Log]

## Git Diff
 Show changes between commits, commit and working tree, etc
*Note:*
*Red Line = Line Removed*
*Green Line = Line Added*

| Commands | Function |
| ------ | ------ |
| `$ git diff` | Main command |
| `$ git diff HEAD` | Same with git diff |
| `$ git diff HEAD^` | Commit before the latest commit |
| `$ git diff HEAD^^` | Previous 2 commits before the latest |
| `$ git diff HEAD~5 ` | 5 previous commit from the latest |
| `$ git diff <SHA> <SHA>` | Diff between 2 different commit with specific <SHA> |
| `$ git diff master <branch>` | Diff between 2 branch |
| `$ git diff --staged` | View staged differences |

## Blame
Purpose: If you can't understand the commit changes, it will list all the revision and the author of each changes
```sh
$ git blame <fileName> --date short
```

## Branching Out
| Commands | Function |
| ------ | ------ |
| `$ git branch` | Will print out in master branch |
| `$ git branch newFeature` | Create new branch |
| `$ git checkout -b newFeature` | Move to newFeature branch |

### Merge your branch to master
```sh
$ git checkout master
$ git merge newFeature
```
*Note: 'Fast-forward' no changes in master branch when the new branch was merged to it*

### Clean up the Feature branch
```sh
$ git branch -d newFeature
```
### Non-Fast-Forward

Situation: When you are working on the feature branch then suddenly you need to fix bugs in the master branch, there will have notification prompted when you try to merge master and feature together.

Sample Scenario:
```sh
$ git checkout -b myFeature2
$ git add .
$ git commit "My new Feature 2"
```
...*Suddenly you need to fix bugs from the master branch while you are working on the feature*
```sh
$ git checkout master
$ git commit -am "Fixing bugs line #53"
```
*Merge the master and feature branch*
```sh
$ git merge newFeature2
```
*There is a VI prompt with this. Just do `:wq` after you make notes*

## Collaboration
**Scenario 1: Working on different file but same remote repo**
1. Person1 push to Github person2 wants a copy and the Person2 wants to add some changes
2. Person2 `git push` to remote after commited some changes in the clone repo
3. Person1 also working on the same repo in his local.
4. Person1 `git push` but FAILED
5. Person1 should `git pull`
6. Person1 then `git push`

**Scenario 2: Working on SAME file and SAME remote repo**
1. Person2 commited changes in file.txt and pushed to remote github repo
2. Person1 commited changes in file.txt to local repo
3. Person1 `git pull`
4. CONFLICT in merge
5. Person1 should edit the file.txt manually
6. Person1 should `git commit -a` to merge commit

### Create a remote branch
**Scenario: Person1 creates new branch to remote**
```sh
git checkout -b myfeature
$ git push origin myfeature // Local branch to remote branch
$ git add .
$ git commit -am "Add new feature"
$ git push //Pushed changes from branch
```
**Person2 wants to work on the new branch**
```sh
$ git pull
$ git branch -r //Show list of all remote branches
$ git checkout myfeature //Auto setup a tracking remote branch
$ git push //Push to remote branch
```
## Tagging
Note: Reference to a commit
Purpose: Release versioning
```sh
$ git tag
$ git checkout v0.0.1
```
### Add new tag
```sh
$ git tag -a v0.0.2 -m "version 0.0.2"
```
### Push new tags
```sh
$ git push --tags
```

## Rebase
Purpose: avoid polluting history when merging branches to master
```sh
$ git rebase
```
Advantages of Rebase:
1. Move all changes to master which are not in origin/master to a temporary area.
2. Run all origin/master commits
3. Run all commits in the temporary area, one at a time

Scenario: What if bugs fixes in master while working on the feature branch
```sh
$ git checkout admin
$ git rebase master
$ git checkout master
$ git merge myfeature
```
Scenario: Modification in same file in master and branch.
```sh
$ git fetch
$ git rebase
```
Resolve the conflict manually and do
```sh
$ git rebase --continue
```
Options: `git rebase --skip` If only we want to skip the changes
Options: `git rebase --abort` If we stop rebasing, ignore all the changes and reset
```sh
$ git status
$ git add file.txt
$ git rebase --continue
```
Scenario: Want to make the branch content upto date and get the commits form master
```sh
$ git checkout branchName
$ git rebase master
```
Note: the commits from the branchName will be placed on the last commit in master HEAD

## Interactive Rebase
Use: 
1. Redo the commits in the branch you are working
`$ git rebase -i HEAD~3` // Commit to replay

2. `pick`: change order of commit
3. `reword`: Rename the commit message
4. `edit`: Split single commit into 2
```sh 
$ git reset HEAD^
$ git add file.txt
$ git commit "Commit 1"
$ git add file2.txt
$ git commit "Commit 2" 
```
5. `squash`: Combine commits into one merges a commit with the previous commit  `git rebase -i HEAD~4`

## Purging History
Use: When you push large or compromised codes like security password, someone's copyright, large files(video, images)
**Note: Need to remove also commit and history**
Steps:
1. **Backup**
    `git clone shop shop-filter`
2. **Rewrite history (Tree Filter)**
`git filter-branch --tree-filter` 
Git will check each commit out into working directory, run your command, and re-commit

## Index Filter

| Commands | Function |
| ------ | ------ |
| `$ git filter-branch --index-filter <command>` | This is command MUST operate on staging area |
| `--index-filter 'rm -f password.txt'` | Operates on working directory only |
| `--index-filter 'git rm --cached --ignore-unmatch password.txt'` | `--ignore-unmatch` succeeds even if the file isn't exist |
| `$ git filter-branch --tree-filter 'rm -f password.txt' ` | By default, you can't run filter-branch again because it won't overwrite the backup |
| `$ git filter-branch -f --tree-filter 'rm -f password.txt'` | you can force it with the -f option |

## Prune empty commits

| Commands | Function |
| ------ | ------ |
| `$ git filter-branch -f --prune-empty -- --all` | Prune all |
| `$ git filter-branch --tree-filter 'rm -f password.txt' --prune-empty -- --all` | Prune during filtering |

## Line Endings

| Commands | Function |
| ------ | ------ |
| `$ git config --global core.autocrlf input` | Changes CR/LF to LF on commit |
| `$ git config --global core.autocrlf true` | Changes LF to CR/LF on checkout (Windows system) |
| `$ git config core.autcrlf false` | Does no conversion (Windows-only projects) |

## Git attribute file
| Commands | Function |
| ------ | ------ |
| `*` | Match any type |
| `*.html` | Match any file in same file-type |
| `text=auto` | Choose conversion automatically |
| `text` | Treat files as text |
| `text eol=crlf` | Convert to specified format on checkout |
| `text eol=lf ` | `eol` = end of line |
| `binary` | Treat files as binary |
| `* text=auto` | Auto convert line endings |
| `*.html text` | Treat image files as binary |
| `*.bat eol=crlf` | Batch in window |

## Cherry-Pick
Get the specific commit from production or dev (no matter what the order of it in history) and use it in dev
```sh
$ git checkout <branchWhereYouWantToCopyTheSpecificCommit>
$ git cherry-pick <sha>
```
### Edit the cherry-pick commit message
```sh
$ git cherry-pick edit <sha>
```
### Multiple cherry pick and combine it
```sh
$ git cherry-pick --no-commit <sha1> <sha2> //--no-commit pulls in changes and stages them, but doesn't commit
$ git commit -m "Combined commit"
```
```sh
$ git cherry-pick -x <sha> //Adds source
$ git cherry-pick --signoff //Adds current user who cherry pick
```

## Submodules
Use: Easily share libraries wihout being outdated
```sh
$ git submodule add git@example.com:css.git
```
### How to modify submodules
```sh
$ cd submodule
$ git checkout master
```
*Note: By default, submodules doesn't have branch. Need explicitly checkout to master branch*
*Make changes
```sh
$ git status
$ git commit -am "Update submodule"
$ git push
```
*Need to go to parent directory to update

## Cloning Projects
```sh
$ git clone git@sample.com:aquarium.git
$ git submodule init
$ git submodule update
$ git merge <sha> //To merge the submodule to the master branch (applicable:headless branch)
```
*go to parent directory
```sh
$ git add.
$ git commit -am "Parent directory"
```
Note: Push twice - submodule and parent
```sh
$ git push --recurse-submodules=on-demand // Push all repositories (even subdirectory)
```

## Reflog
Use: Log in local repo
```sh
$ git reflog
$ git reset -hard <sha> or git reset --hard HEAD@{1} //Restore using this command
```
You cannot retrieve deleted branch but not 
```sh
$ git log --walk-reflogs // detailed full log
```

#### Reference

See [GIT](http://git-scm.com)


## Author

* **Ann G.** ⊂(・﹏・⊂) [Adebugslife](http://adebugslife.com)


License
----

GNU General Public License v3.0

**Free Reference, Hell Yeah! (￣▽￣)ゞ**

   [Git Log]: <https://git-scm.com/docs/git-log>
   [Git Alias]: <https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases>
   [Git Configuration]: <https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration>
   [Git Help]: <https://git-scm.com/docs/git-help>
   [Git Clean]: <https://git-scm.com/docs/git-clean>

