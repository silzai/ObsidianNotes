- To use git on even a single file, we need to initialize a repository.
- `git init` to initialize
- `git status` to check-in on the repo, will be able to see the commits.
- commit is a check-point, to commit, first do `git add <file name>` into the staging area.
##### there are different ways to commit:
- `git commit -m "message"`  -m flag will only create a commit and display the message.
- once you have commited, you can write `git log` which will give you a history of commits.
##### to go back and forth in code changes 
- `git checkout <hash of commit that you wnat to go back to>` will let you go back and forth to points in your code. 
- `git branch` will tell me which hash I am on.
- and `git status` will tell me which branch I am on.
- branch master is the default branch that contains the latest and final code.
- To go to the latest code you wrote from a previous checkout, write `git checkout master`.
##### Create new branch
- `git branch <branchName>` will create a new branch.
- `git checkout <branchName>` will move the code to a new branch so you can make any new or additional changes there.
- if you do `git log`, on branch master, you will not see the commits from the new branch, unless you merge.
- Now if you `git checkout` back to the master branch, after making changes to a new branch, you will return to the old code you wrote in the master branch.
##### To merge new/additional branch into master branch if you are satisfied with it
- to merge the additional branch into branch master, do `git merge <branchName>`
- Now if you do `git log`, you will see the changes in from the new branch in branch master as well.