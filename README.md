Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
    <img alt="Git" src="./Img/git-logo.png" height="190" width="455">
</p>
<hr>

# Other Available Language:

[Arabic Git Cheat Sheet](https://github.com/abdozargina/git-github/blob/main/other-sheets/git-cheat-sheet-ar.md

Git cheat sheet saves you from learning all the commands by heart.

Be free to contribute, update the grammar mistakes. You are also free to add your language file.

<hr>

Git Cheat Sheet English
===============
### Index
* [Set Up](#setup)
* [Configuration Files](#configuration-files)
* [Create](#create)
* [Local Changes](#local-changes)
* [Search](#search)
* [Commit History](#commit-history)
* [Branches & Tags](#branches--tags)
* [Update & Publish](#update--publish)
* [Merge & Rebase](#merge--rebase)
* [Undo](#undo)
* [Git Flow](#git-flow)


<hr>

## Setup

##### Show current configuration:
```
$ git config --list
```
##### Show repository configuration:
```
$ git config --local --list
```

##### Show global configuration:
```
$ git config --global --list
```

##### Show system configuration:
```
$ git config --system --list
```

##### Set a name that is identifiable for credit when review version history:
```
$ git config --global user.name "[firstname lastname]"
```

##### Set an email address that will be associated with each history marker:
```
$ git config --global user.email "[valid-email]"
```

##### Set automatic command line coloring for Git for easy reviewing:
```
$ git config --global color.ui auto
```

##### Set global editor for commit
```
$ git config --global core.editor vi
```

<hr>

## Configuration Files

##### Repository specific configuration file [--local]:
```
<repo>/.git/config
```

##### User-specific configuration file [--global]:
```
~/.gitconfig
```

##### System-wide configuration file [--system]:
```
/etc/gitconfig
```

<hr>

## Create

##### Clone an existing repository:

There are two ways:

Via SSH

```
$ git clone ssh://user@domain.com/repo.git
```

Via HTTP

```
$ git clone http://domain.com/user/repo.git
```

##### Create a new local repository in the current directory:
```
$ git init
```

##### Create a new local repository in a specific directory:
```
$ git init <directory>
```

<hr>

## Local Changes

##### Changes in working directory:
```
$ git status
```

##### Changes to tracked files:
```
$ git diff
```

##### See changes/difference of a specific file:
```
$ git diff <file>
```

##### Add all current changes to the next commit:
```
$ git add .
```

##### Add some changes in &lt;file&gt; to the next commit:
```
$ git add -p <file>
```

##### Add only the mentioned files to the next commit:
```
$ git add <filename1> <filename2>
```

##### Commit all local changes in tracked files:
```
$ git commit -a
```

##### Commit previously staged changes:
```
$ git commit
```

##### Commit with message:
```
$ git commit -m 'message here'
```

##### Commit skipping the staging area and adding message:
```
$ git commit -am 'message here'
```

##### Commit to some previous date:
```
$ git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

##### Change last commit:<br>
<em><sub>Don't amend published commits!</sub></em>

```
$ git commit -a --amend
```

##### Amend with last commit but use the previous commit log message
<em><sub>Don't amend published commits!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### Change committer date of last commit:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### Change Author date of last commit:
```shell
$ git commit --amend --date="date"
```

##### Move uncommitted changes from current branch to some other branch:<br>
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### Restore stashed changes back to current branch:
```shell
$ git stash apply
```

#### Restore particular stash back to current branch:
- *{stash_number}* can be obtained from `git stash list`

```shell
$ git stash apply stash@{stash_number}
```

##### Remove the last set of stashed changes:
```
$ git stash drop
```

<hr>

## Search

##### A text search on all files in the directory:
```
$ git grep "Hello"
```

##### In any version of a text search:
```
$ git grep "Hello" v2.5
```

##### Show commits that introduced a specific keyword
```
$ git log -S 'keyword'
```

##### Show commits that introduced a specific keyword (using a regular expression)
```
$ git log -S 'keyword' --pickaxe-regex
```

<hr>

## Commit History

##### Show all commits, starting with newest (it'll show the hash, author information, date of commit and title of the commit):
```
$ git log
```

##### Show all the commits(it'll show just the commit hash and the commit message):
```
$ git log --oneline
```

##### Show all commits of a specific user:
```
$ git log --author="username"
```

##### Show changes over time for a specific file:
```
$ git log -p <file>
```

##### Display commits that are present only in remote/branch in right side
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### Who changed, what and when in &lt;file&gt;:
```
$ git blame <file>
```

##### Show Reference log:
```
$ git reflog show
```

##### Delete Reference log:
```
$ git reflog delete
```
<hr>

## Move / Rename

##### Rename a file:

Rename Index.txt to Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## Branches & Tags

##### List all local branches:
```
$ git branch
```

#### List local/remote branches
```
$ git branch -a
```

##### List all remote branches:
```
$ git branch -r
```

##### Switch HEAD branch:
```
$ git checkout <branch>
```

##### Checkout single file from different branch
```
$ git checkout <branch> -- <filename>
```

##### Create and switch new branch:
```
$ git checkout -b <branch>
```

##### Switch to the previous branch, without saying the name explicitly:
```
$ git checkout -
```

##### Create a new branch from an exiting branch and switch to new branch:
```
$ git checkout -b <new_branch> <existing_branch>
```


#### Checkout and create a new branch from existing commit
```
$ git checkout <commit-hash> -b <new_branch_name>
```


##### Create a new branch based on your current HEAD:
```
$ git branch <new-branch>
```

##### Create a new tracking branch based on a remote branch:
```
$ git branch --track <new-branch> <remote-branch>
```

##### Delete a local branch:
```
$ git branch -d <branch>
```

##### Rename current branch to new branch name
```shell
$ git branch -m <new_branch_name>
```

##### Force delete a local branch:
<em><sub>You will lose unmerged changes!</sub></em>

```
$ git branch -D <branch>
```

##### Mark `HEAD` with a tag:
```
$ git tag <tag-name>
```

##### Mark `HEAD` with a tag and open the editor to include a message:
```
$ git tag -a <tag-name>
```

##### Mark `HEAD` with a tag that includes a message:
```
$ git tag <tag-name> -am 'message here'
```

##### List all tags:
```
$ git tag
```

##### List all tags with their messages (tag message or commit message if tag has no message):
```
$ git tag -n
```

<hr>

## Update & Publish

##### List all current configured remotes:
```
$ git remote -v
```

##### Show information about a remote:
```
$ git remote show <remote>
```

##### Add new remote repository, named &lt;remote&gt;:
```
$ git remote add <remote> <url>
```

##### Rename a remote repository, from &lt;remote&gt; to &lt;new_remote&gt;:
```
$ git remote rename <remote> <new_remote>
```

##### Remove a remote:
```
$ git remote rm <remote>
```

<em><sub>Note: git remote rm does not delete the remote repository from the server. It simply removes the remote and its references from your local repository.</sub></em>

##### Download all changes from &lt;remote&gt;, but don't integrate into HEAD:
```
$ git fetch <remote>
```

##### Download changes and directly merge/integrate into HEAD:
```
$ git remote pull <remote> <url>
```

##### Get all changes from HEAD to local repository:
```
$ git pull origin master
```

##### Get all changes from HEAD to local repository without a merge:
```
$ git pull --rebase <remote> <branch>
```

##### Publish local changes on a remote:
```
$ git push <remote> <branch>
```

##### Delete a branch on the remote:
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
OR
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

##### Publish your tags:
```
$ git push --tags
```
<hr>

#### Configure the merge tool globally to meld (editor)
```bash
$ git config --global merge.tool meld
```

##### Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

## Merge & Rebase

##### Merge branch into your current HEAD:
```
$ git merge <branch>
```

#### List merged branches
```
$ git branch --merged
```

##### Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>

```
$ git rebase <branch>
```

##### Abort a rebase:
```
$ git rebase --abort
```

##### Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

##### Use your editor to manually solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

##### Squashing commits:
```
$ git rebase -i <commit-just-before-first>
```

Now replace this,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

to this,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## Undo

##### Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

##### Get all the files out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

##### Discard local changes in a specific file:
```
$ git checkout HEAD <file>
```

##### Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

##### Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

##### Reset your HEAD pointer to a remote branch current state.
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

##### Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

##### Remove files that were accidentally committed before they were added to .gitignore
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

## Git-Flow
Improved [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Index
* [Setup](#setup)
* [Getting Started](#getting-started)
* [Features](#features)
* [Make a Release](#make-a-release)
* [Hotfixes](#hotfixes)
* [Commands](#commands)

<hr>

### Setup
###### You need a working git installation as prerequisite. Git flow works on OSX, Linux and Windows.

##### OSX Homebrew:
```
$ brew install git-flow-avh
```

##### OSX Macports:
```
$ port install git-flow
```

##### Linux (Debian-based):
```
$ sudo apt-get install git-flow
```

##### Windows (Cygwin):
###### You need wget and util-linux to install git-flow.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Getting Started
###### Git flow needs to be initialized in order to customize your project setup. Start using git-flow by initializing it inside an existing git repository:
##### Initialize:
###### You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```shell
git flow init
```
OR
###### To use default
```shell
git flow init -d
```
<hr>

### Features
###### Develop new features for upcoming releases. Typically exist in developers repos only.
##### Start a new feature:
###### This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

##### Finish up a feature:
###### Finish the development of a feature. This action performs the following:
###### 1) Merged MYFEATURE into 'develop'.
###### 2) Removes the feature branch.
###### 3) Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

##### Publish a feature:
###### Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

##### Getting a published feature:
###### Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

##### Tracking a origin feature:
###### You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>

### Make a Release
###### Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

##### Start a release:
###### To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
###### It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
###### (You can track a remote release with the: ```git flow release track RELEASE``` command)

##### Finish up a release:
###### Finishing a release is one of the big steps in git branching. It performs several actions:
###### 1) Merges the release branch back into 'master'
###### 2) Tags the release with its name
###### 3) Back-merges the release into 'develop'
###### 4) Removes the release branch
```
git flow release finish RELEASE
```
###### Don't forget to push your tags with ```git push --tags```

<hr>

### Hotfixes
###### Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

##### Git flow hotfix start:
###### Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
###### The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

##### Finish a hotfix:
###### By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>

### Commands
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow schema

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>

# Let's summarize the previous commands simply 

## 1. Most used Commands
 
   ## Setup
| Description | Command | 
|--|--|
|See where Git is located|`which git`|
|Get the version of Git|`git --version`|
|Create an alias (shortcut) for `git status`  |`git config --global alias.st status`|
|Help |`git help`|

## General
| Description | Command | 
|--|--|
| Initialize Git| `git init`|
|Get everything ready to commit| `git add .`|
|Get custom file ready to commit |`git add index.html`|
|Commit changes|`git commit -m "Message"`|
|Commit changes with title and description| `git commit -m "Title" -m "Description..."`|
|Add and commit in one step|`git commit -am "Message"`|
|Remove files from Git|`git rm index.html`|
|Update all changes|`git add -u`|
|Remove file but do not track anymore|`git rm --cached index.html`|
|Move or rename files|`git mv index.html dir/index_new.html`|
|Undo modifications (restore files from latest commited version)|`git checkout -- index.html`|
|Restore file from a custom commit (in current branch)|`git checkout 6eb715d -- index.html`|

## Branch
| Description | Command | 
|--|--|
|Show branches|`git branch`|
|Create branch|`git branch branchname`|
|Change to branch|`git checkout branchname`|
|Create and change to new branch|`git checkout -b branchname`|
|Rename branch|`git branch -m branchname new_branchname` or  `git branch --move branchname new_branchname`|
|Show all completely merged branches with current branch|`git branch --merged`|
|Delete merged branch (only possible if not HEAD)|`git branch -d branchname` or  `git branch --delete branchname`|
|Delete not merged branch|`git branch -D branch_to_delete`|

## Log
| Description | Command | 
|--|--|
|Show commits|`git log`|
|Show oneline-summary of commits|`git log --oneline`|
|Show oneline-summary of commits with full SHA-1|`git log --format=oneline`|
|Show oneline-summary of the last three commits|`git log --oneline -3`|
|Show only custom commits|`git log --author="Sven"` `git log --grep="Message"` `git log --until=2013-01-01` `git log --since=2013-01-01`|
|Show only custom data of commit| `git log --format=short`  `git log --format=full`  `git log --format=fuller`  `git log --format=email`  `git log --format=raw`  |
|Show changes|`git log -p`|
|Show every commit since special commit for custom file only|`git log 6eb715d.. index.html`|
|Show changes of every commit since special commit for custom file only|`git log -p 6eb715d.. index.html`|
|Show stats and summary of commits|`git log --stat --summary`|
|Show history of commits as graph|`git log --graph`|
|Show history of commits as graph-summary|`git log --oneline --graph --all --decorate`|

## Compare
| Description | Command | 
|--|--|
|Compare modified files|`git diff`|
|Compare modified files and highlight changes only|`git diff --color-words index.html`
|Compare modified files within the staging area|`git diff --staged`|
|Compare branches|`git diff master..branchname`|
|Compare branches like above|`git diff --color-words master..branchname^`|
|Compare commits| `git diff 6eb715d`  `git diff 6eb715d..HEAD`  `git diff 6eb715d..537a09f`  |
|Compare commits of file|`git diff 6eb715d index.html`  `git diff 6eb715d..537a09f index.html`|
|Compare without caring about spaces| `git diff -b 6eb715d..HEAD` or `git diff --ignore-space-change 6eb715d..HEAD`|
|Compare without caring about spaces| `git diff -b 6eb715d..HEAD` or `git diff --ignore-space-change 6eb715d..HEAD`|
|Compare without caring about spaces| `git diff -b 6eb715d..HEAD` or `git diff --ignore-space-change 6eb715d..HEAD`|
|Compare without caring about all spaces|`git diff -w 6eb715d..HEAD` or `git diff --ignore-all-space 6eb715d..HEAD`|
|Useful comparings|`git diff --stat --summary 6eb715d..HEAD`|
|Blame|`git blame -L10,+1 index.html` |

## Merge
| Description | Command | 
|--|--|
|True merge (fast forward)|`git merge branchname`|
|Merge to master (only if fast forward)|`git merge --ff-only branchname`|
|Merge to master (force a new commit)|`git merge --no-ff branchname`|
|Stop merge (in case of conflicts)|`git merge --abort`|
|Stop merge (in case of conflicts)|`git reset --merge` // prior to v1.7.4|
|Undo local merge that hasn't been pushed yet|`git reset --hard origin/master`|
|Merge only one specific commit |`git cherry-pick 073791e7`|
|Rebase|`git checkout branchname` » `git rebase master` or  `git merge master branchname`
(The rebase moves all of the commits in `master` onto the tip of `branchname`.)|
|Cancel rebase|`git rebase --abort`|
|Squash multiple commits into one|`git rebase -i HEAD~3` ([source](https//www.devroom.io/2011/07/05/git-squash-your-latests-commits-into-one/))|
|Squash-merge a feature branch (as one commit)|`git merge --squash branchname` (commit afterwards)|

## Reset
| Description | Command | 
|--|--|
|Go back to commit|`git revert 073791e7dd71b90daa853b2c5acc2c925f02dbc6`|
|Soft reset (move HEAD only; neither staging nor working dir is changed)|`git reset --soft 073791e7dd71b90daa853b2c5acc2c925f02dbc6`|
|Undo latest commit |`git reset --soft HEAD~ `|
|Mixed reset (move HEAD and change staging to match repo; does not affect working dir)|`git reset --mixed 073791e7dd71b90daa853b2c5acc2c925f02dbc6`|
|Hard reset (move HEAD and change staging dir and working dir to match repo)|`git reset --hard 073791e7dd71b90daa853b2c5acc2c925f02dbc6`|
|Hard reset of a single file (`@` is short for `HEAD`)|`git checkout @ -- index.html`|

## Update & Delete
| Description | Command | 
|--|--|
|Test-Delete untracked files|`git clean -n`|
|Delete untracked files (not staging)|`git clean -f`|
|Unstage (undo adds)|`git reset HEAD index.html`|
|Update most recent commit (also update the commit message)|`git commit --amend -m "New Message"`|

## Stash
| Description | Command | 
|--|--|
|Put in stash|`git stash save "Message"`|
|Show stash|`git stash list`|
|Show stash stats|`git stash show stash@{0}`|
|Show stash changes|`git stash show -p stash@{0}`|
|Use custom stash item and drop it|`git stash pop stash@{0}`|
|Use custom stash item and do not drop it|`git stash apply stash@{0}`|
|Use custom stash item and index|`git stash apply --index`|
|Create branch from stash |`git stash branch new_branch`|
|Delete custom stash item|`git stash drop stash@{0}`|
|Delete complete stash|`git stash clear`|

## Releases & Version Tags
| Description | Command | 
|--|--|
|Show all released versions|`git tag`|
|Show all released versions with comments|`git tag -l -n1`|
|Create release version|`git tag v1.0.0`|
|Create release version with comment|`git tag -a v1.0.0 -m 'Message'`|
|Checkout a specific release version|`git checkout v1.0.0`|

## Collaborate
| Description | Command | 
|--|--|
|Show remote|`git remote`|
|Show remote details|`git remote -v`|
|Add remote upstream from GitHub project|`git remote add upstream https//github.com/user/project.git`|
|Add remote upstream from existing empty project on server|`git remote add upstream ssh//root@123.123.123.123/path/to/repository/.git`|
|Fetch|`git fetch upstream`|
|Fetch a custom branch|`git fetch upstream branchnamelocal_branchname`|
|Merge fetched commits|`git merge upstream/master`|
|Remove origin|`git remote rm origin`|
|Show remote branches|`git branch -r`|
|Show all branches (remote and local)|`git branch -a`|
|Create and checkout branch from a remote branch|`git checkout -b local_branchname upstream/remote_branchname`|
|Compare|`git diff origin/master..master`|
|Push (set default with `-u`)|`git push -u origin master`|
|Push|`git push origin master`|
|Force-Push|`git push origin master --force`|
|Pull|`git pull`|
|Pull specific branch|`git pull origin branchname`|
|Fetch a pull request on GitHub by its ID and create a new branch|`git fetch upstream pull/ID/headnew-pr-branch`|
|Clone to localhost|`git clone https//github.com/user/project.git`   or   `git clone ssh//user@domain.com/~/dir/.git`|
|Clone to localhost folder|`git clone https//github.com/user/project.git ~/dir/folder`|
|Clone specific branch to localhost|`git clone -b branchname https//github.com/user/project.git`|
|Clone with token authentication (in CI environment)|`git clone https//oauth2<token>@gitlab.com/username/repo.git`|
|Delete remote branch (push nothing)|`git push origin branchname` or `git push origin --delete branchname`|

## Archive
| Description | Command | 
|--|--|
|Create a zip-archive |`git archive --format zip --output filename.zip master`|
|Export/write custom log to a file |`git log --author=sven --all > log.txt`|

## Gitignore & Gitkeep
| Description | Command | 
|--|--|
|Add or edit gitignore |`nano .gitignore`|
|Track empty dir |`touch dir/.gitkeep`|

[About .git ignore](https://docs.github.com/en/github/using-git/ignoring-files)  
[Useful templates](https://github.com/github/gitignore)

## Large File Storage
Website https//git-lfs.github.com/
| Description | Command | 
|--|--|
|Install| `brew install git-lfs`|

Track `*.psd` files `git lfs track "*.psd"` (init, add, commit and push as written above)

## Reference
- [Documentations](https://git-scm.com/doc)
- [Related Pro Tips](https//ochronus.com/git-tips-from-the-trenches/)
- [videos](https://git-scm.com/videos)
- [Interactive Beginners Tutorial](https://ndpsoftware.com/git-cheatsheet.html)
- [Git Cheatsheet](https://github.github.com/training-kit/)
- [Complete list of all commands](https://git-scm.com/docs/git#_git_commands)

      

## 2. Your first repository


   - Configuration 
   
        - ```
            $ git config --global user.name "githubUsername"
            $ git config --global user.email "Foulen@Domaine.com"
          ```
      
   - Create New Repository in github 
       ![create repo](https://user-images.githubusercontent.com/89027268/152925946-49d3d722-378a-44c2-8218-eb33443f6121.PNG)
       <img width="252" alt="newrepo0" src="https://user-images.githubusercontent.com/89027268/152925976-9128c85f-8e8d-4bdb-9052-b29aecc7cc20.png">

   - Clone the Repository in your Local machine 
      - `
            $ git clone https://github.com/userName/RepoName.git
        `
   - Open the folder and start your project
   - Add changes to the staging Area
      - ` $ git add . `
   - Commit changes 
      - ` $ git commit -m "commit message" `
   - Push changes to remote 
      - ` $ git push `

# Simple abbreviation for most of the previous commands in the pictures below

<p align="center">
    <img alt="Git" src="https://user-images.githubusercontent.com/89027268/152922314-9a5e8744-7f11-4209-a565-84e114ea7d5e.png">
    <img alt="Git" src="https://raw.githubusercontent.com/MikeRodeman/Git-Cheat-Sheet/master/Light%20Mode/PNG%20Files/Cropped/Git%20Cheat%20Sheet%20-%20Light%20Mode%20-%20Cropped%20-%20Page%201%20of%204.png">
    <img alt="Git" src="https://raw.githubusercontent.com/MikeRodeman/Git-Cheat-Sheet/master/Light%20Mode/PNG%20Files/Cropped/Git%20Cheat%20Sheet%20-%20Light%20Mode%20-%20Cropped%20-%20Page%202%20of%204.png">
    <img alt="Git" src="https://raw.githubusercontent.com/MikeRodeman/Git-Cheat-Sheet/master/Light%20Mode/PNG%20Files/Cropped/Git%20Cheat%20Sheet%20-%20Light%20Mode%20-%20Cropped%20-%20Page%203%20of%204.png">
    <img alt="Git" src="https://raw.githubusercontent.com/MikeRodeman/Git-Cheat-Sheet/master/Light%20Mode/PNG%20Files/Cropped/Git%20Cheat%20Sheet%20-%20Light%20Mode%20-%20Cropped%20-%20Page%204%20of%204.png">
</p>
<hr>

