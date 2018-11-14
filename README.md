# modified => staging => committed

## GIT commands
* `git status` => gives us status about the files modified
* `touch index.html` => creates index file

## creating a repository (local)
* cd (location of the folder where a git is to be initialized)
* `git init` 

## staging files
* `git add index.html`(filename)  => adds index.html to staging area
* `git add .` => adds all the modified files to staging area 

## commiting files
* `git commit -m "message about the commit"`
* `git log` => shows commit history
* `git log --oneline` => shows commit history in short form

* **NOTE:** latest commit is at the top

## Undoing things
### checkout 
*	`git checkout <code>` => takes to the commit history thru its code
*	`git checkout master` => takes to the master branch

### revert
*	`git revert <code>` => don't delete the commit but reverts the commit on the code. Enters in a box. Type ":WQ" to exit the box.

### reset
*	`git reset <code>` => unstages the files on the commited code
*	`git reset <code> --hard` => deletes all the commits upto that code and switches to the branch named as (`HEAD detached at <code>`).

### *for remote repository*
* `git push origin +HEAD^:<name of your branch, most likely 'master'>` => This removes the recent commit from the remote repo of github.

## Branches

* `git branch <branch name>` => creates a new branch but stays in master
* `git branch -a` => shows list of branches
* `git checkout <branchname>` => switch to a particular branch
* `git checkout -b <branchname>` => creates a new branch and switches to it from master branch.

### To delete a branch, first move to master branch then:  
* `git branch -D <branchname>` => deletes a branch. (lowercase d incase when the branch to be deleted is already merged)

## Overwriting master with other branch

first stay on the branch(not master) then:
1. `git branch -f master <branch name>` will rewrite local master branch.

2. `git push remote <branch name>:master` will rewrite remote branch.


## Merging branches(& conflicts)

* First switch to master branch then:  
`git merge <branchname>` => merges the specific branch to master branch

**NOTE:** Incase person1 commits a change in master branch while person 2 is unaware of it, Person 2 merges his branch to the master branch. conflict occurs.
1. keep the file to staging area.  => `git add .`
2. `git commit` (no need to specify message). Takes u to a box (same as that in revert). Type "`:wq`".

## Github commands

Note:	
* create a repository :
	1. with same name as the project existing in computer ( no need of READme file )
	2. directly in github ( initialize the READme file ). Also clone the repo to the computer. => `git clone <URL for remote repo>`
( local repo: in computer; remote repo: in github)

* *edit*, *stage*, *commit* all the changes in file.

### If STEP 1 is used to create repo
* PUSH command => `git push <URL for remote repository>`

### alt and best way:
(put an alias "origin" ;default alias for github)
* `git remote add origin <URL for remote repository>`
* `git push origin`

### If STEP 2 is used to create repo:
* get list of "origin" alias => `git remote -v`

### PUSH command
`git push origin master`

## COLLABORATING in github

## Working on a new feature:
1. `git pull origin master` => fetches all the code from remote repo, keeps code up to date

2. `git checkout -b <branchname>` => creates a new branch to work upon a feature

3. commit changes then:

`git push origin <branchname>` => pushes the branch(feature) to the remote repo for other developers to review it and probably merge it. 

If they merge it, it stays in the master branch of remote repo. So we have to *PULL* master again to work on the next feature everytime.    

## Pushing branch to remote repo
1. switch to the branch u want to push, then

`git push -u origin <branch>`// u short for `--set-upstream` => which makes branches trackable.
**NOTE:** replace <branch> with HEAD to avoid naming error


## FORKING(& contributing)  
working on open sources or others project
