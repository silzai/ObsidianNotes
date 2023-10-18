##### To upload local git repo to GitHub
- we have to `push`.
- First we have to make a new repository in GitHub.
- Second, we will go to local git repo and tell git that I want to save the changes to GitHub online as well, to do that I will do `git remote add origin (origin is just the name of the remote) <URL of GitHub repo>` 
	- `git remote -v` will list the remotes that I have.
- Now to send the local code to GitHub, we have to `push` the code.
	- do `git push -u origin master` to push/upload the branch 'master' into GitHub using remote 'origin'.
##### To get the changes from GitHub made by a collaborator into my local repo
- we have to `pull`.
- do `git pull origin master` to pull/download the changes made in GitHub by another person into my local repo. 
	- again, 'origin' is the URL and 'master' is the branch.
#### Cloning VS Forking
- Forking is "GitHub" specific i.e. it is not a command on Git, and we can fork a public repo, then pull it, and do any changes and push.
- Cloning is like "pulling" the public repo, but we cannot do any changes on it (if not allowed), but only use it locally.