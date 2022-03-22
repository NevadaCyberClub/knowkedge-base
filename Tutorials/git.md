# How to use Git

## About Git
### What is Git? 


### Termonology
Branch 
commit
pointer
commit hash


### How does Git work
Git generates a checksum for each change set
Git uses SHA-1 the hash algorithm to create checksums - 40 characters hexadecimal string
Simple way to come up with rather unique identifiers to commits
A series of commits is linked together since each commit points to its parent commit unless it is the initial commit along with other information like the author and message



## Initial setup

First setup your identity. Each time you commit to a repository it adds this information toit. This is usefull when you want to trace back who ,ade a change to a particular piece of code. Use the following command to setup ypue identity:   

```
$ git config --global user.name "Your Name"
$ git config --global user.email yourEmail@example.com
```

Next you will want to let know Git what is your prefered editor (else its going to use Vim which you may not know how to use):
```
$ git config --global core.editor nano 
```
Substitute `nano`  with your editor of choice.   


### Branches/pointers

HEAD
Master
### Creating a branch
#### Creating branch from another branch or commit hash

### Moving around
#### move back in time to a previous commit where there is no pointer


### staging the files 
### Commit mesages


### Commit history




## Remote repositories
In the initial part of this tutorial you worked locally. In this section you will be working with remote repositories. Essentially, it is copying/syncing your local repository with a remote server, This allows multiple people to work on the code at once. Merge conflicts are managed locally. The default name for your first remote server ina repository is `origin`. Your local repository can point to multiple remote locations, for example, one can push code to a backup code server, a production server, a developemnt server ...etc.

### Most common providers
You can register for an account on their respective websites.

- Github
- Gitlab
- Bitbucket

### Terminology
Pull 
fetch
Clone 
Merge
Commit
### Configuring credentials 
Credentials allow you to authenticate with the foreign server as the remote server will not allow anyone to edit the code (just the authorized individuals) and if the code is provate it may not allow anyone to pull from the code.
There are two methods, one is using HTTPS, the other is using SSH. HTTPS is just using your username and password for the remote repo. SSH is just like SSH key authentication, you share your public key with the remote server and the system takes cares of auth using your keys.

HTTPS is easier, but you have to login eveytime authentication is required. Which is what we are going to use for this tutorial. SSH has more initial setup, but after that you can forget about it.

More info on SSH setup [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh).

### Adding a remote location 
remote -v 
remote add origin 

### Pulling 
### Fetching
### Pushing 



You can do multiple commits without sycing eveytime, just push whenever you think its appropate.
You can push to any branch you woud like, by default its the defaul set in your remote server, usually master. Sometimes in the remote server master is a protected branch, meaning you cant edit it directly, you have to push to another branch and merge it int eh remote server (usually via gui, or via termianal using the force flags). 

The first inital push you will set your local branch to track a remote branch with the `-u`/`--set-upstream`  flag (or you can use the `git branch -u` comand to achieve the same without pushing)
git push -u origin main



### merging 

# Tasks
- Configure identity
- Configure editor
- Create a local repository
- Create a new branch named `dev`
- Switch to new branch `dev` 
- Switch to `master` (just to get a feel for how to move around)
- Create new file and add something to it (like code)
- Stage and commit changes
- Edit the file again, stage and commit changes (essentially create two commits)
- View your commit history 
- Pick a commit in the past and copy its commit hash
- Switch to the commit using the commit hash, essentially move back in time to a previous commit where there is no pointer
- Browse around, you will see that your old files are there
- When you are ready to go back switch to `dev` or `master`
- Since we have mutliple commits we can now push them to a remote server
- Create an account with Github if you dont already have one
- Create a new empty repository 
- Copy the repo URI
- Add the remote repo to you local repo 
- Push to the repo and set branch to track the remote
   - If your remote was not empty then you will have to pull first and or merge if nesesary
- After pushing you can see your changes online
- now lets simulate changes by soeone else
- Lets go online and so come changes to the files vie the web interface
- then we can do a pull and our repo will be updates locally



# Sources 
