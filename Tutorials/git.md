This is more a knowledge dump more than anything. Git is very complex and this file does not even scratch the surface. I encourage you to read this more than once as topics rely on later topics and vice versa. It will make more sense as you read it more than once. If I linked an externa page then its more of an advanced topic, so if its your first time using Git then skip it for now and come after you feel more confortable. 

I have added a link to a good workshop I found at the end. If you want to learn a bit more read on, if you want to learn just how to use it skip to the end.

Also pardon my spelling, I had no spelling cheking when I wrote this. If you want to fix somthing, hopefuly after reading this you will be able to submit a pull request to this remote repository. More about contributing [here](https://github.com/NevadaCyberClub/knowkedge-base/blob/master/CONTRIBUTING.md#contributing-procedure).

##### Terminal/command line argument primer
For those new to terminal commands, when you see angled brackets (for example `<name>`) it means a required argument (user supplied value), so replace the whole thing. For example `<name>` replace with `john`. If it is square brackets (for example `[last_name]`) then it is an optional value, you can either choose to put a value there or not, for example `[last_name]` can be the last name `doe` or skip it all together. 

# Git
## About Git
### What is Git? 
"Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency." - [git-scm.com](https://git-scm.com/)   

A version control system helps manage different project versions. It is specially useful when working with muliple users in teh same project. Project here generally means code. 


#### Git vs Github
"The key difference between Git and GitHub is that Git is an open-source tool developers install locally to manage source code, while GitHub is an online service to which developers who use Git can connect and upload or download resources." - [source here](https://www.theserverside.com/video/Git-vs-GitHub-What-is-the-difference-between-them#:~:text=The%20key%20difference%20between%20Git,and%20upload%20or%20download%20resources.)


### Terminology
By reading this article you should get familiar with the following terminology, here is quick definitions to help you navigate yourself around, for more information read on.
| Term | Description|
|:--:|--|
|Repository| Git repository (or repo) tracks and saves the history of all changes made to the files in a Git project
|Commit| A snapshot of the project|
|Branch | A particular timeline, see pointer|
|Pointer | A label pointing to a commit hash on a branch
|Commit hash| A way to reliably identify each commit using SHA-1 algorithm


### How does Git work
Its very clever.
When you create a change it takes the difference of the current file and the previous version of that file and creates, it does this for evey file and this constitudes a commit. Put all the commits together and you have a branch.

<!--
Each commit is unique.
Git generates a checksum for each change set
Git uses SHA-1 the hash algorithm to create checksums - 40 characters hexadecimal string
Simple way to come up with rather unique identifiers to commits
A series of commits is linked together since each commit points to its parent commit unless it is the initial commit along with other information like the author and message
-->


## Initial setup

First setup your identity. Each time you commit to a repository it adds this information to it. Git will tell you to do this when you use it, so why not do it now. Its a one time setup. Online git repository website often use you email in a commit to link them to a particular account. 

Use the following command to setup your identity:   

```
$ git config --global user.name "Your Name"
$ git config --global user.email yourEmail@example.com
```

Next you will want to let know Git what is your prefered editor (else its going to use Vim which you may not know how to use):
```
$ git config --global core.editor nano 
```
Substitute `nano`  with your editor of choice.   


### What is tracking?
Git is amazing but you need to tell it what you want. Before Git can track your files for you you have to let it know that it needs to know that. To do that we add and commit the file once, after that Git will track it for you. You can verify that it is tracking certain file by using teh `git status` command, if it lists it as untracked then its not tracked. 

In this context we talk about file tracking and not branch tracking 

One thing to mentioned about tracked and untracked files. This will make more sense when you read the rest of this document. If a file is tracked Git can change its file contents when you change branches. Lets say you got back in history, now that particular tracked file will change to the previous version. As for untracked files, git will leave them alone. Git will not just let you lose your changes when you changes branches like that, ti will tell you hey I cant changes branches since I am going to change the file for you since you have incommited chagnes, please fix that and try again later. This is where a command like `git stash` comes into play, we wont get into deailts here but it essentially lets you temporarely stash away your work so you can do stuff, and when you are ready you can bring your uncommtied stuff back 


### What is staging?
Git is awesome and it allows you to pick and chose what you want to add into a commit. Before you can commit a change you have to tell Git what things you want to add into the commit. You do this by staging. Staging is the process of telling Git what is it that needs to be added in the next commit you want to make. 
Git 

allos you to work on you files however you like, once you are ready to make a commit. 
Git is amaxStaging


### What is a commit?
A commit is point in time where we wanted to snapshot the current state of the project. Git does this by saving the difference from the previous commit and saving it as a commit. Essentially Git saves as sequence of differences that can later be used to recontruct the state of things. If you have taken Algorithms class you pribably have heard of graphs, commits are nodes in a graph.

On a side note here, Git has the `git diff` command that allows you view/create the differences between files in different commits. You can also generate `patches` which are e-mailable changes of these file. Fun fact, Linux development uses this process of emailing changes to the mantainers. This is more of a intermediate evel topic, wont be covered in detail here.

![git graph showing pointers](images/git/pointer.png)


A commit is referenced by its hash (not in the above picture). This hash is created using the SHA-1 hashing algorithm on that particular commit/patch. Hashes have to froms:
- The long form 
   - Full sha-1 hash of the commit
   - looks like: `97dd2ae065771908ee9ae0fa08ccdb58b5a6b18f` 
- The short form 
   - The last 7 digits of the longs form by default
   - Looks like: `5a6b18f`

You will probably will not need to know this unless you are curious [here is how they create it the hash](https://gist.github.com/masak/2415865).

You are welcome to use either one inside of Git as having two commits with the same hash ending is pretty slim. But if for some reason they do use the long. In most places where you can use a commit hash you can also use a branch name (more on that later), but then again use common sense.

Each commit is identified with who made it. This is where your ientity comes in. There is this tool called `git blame` that leats you find who was responsable for a particular change (even by line number) on a particular file. Its awesome when you need to know who made the file if you need help or even find who added a bug hence blame. If you would like to read more about it read the [git blame documentation](https://git-scm.com/docs/git-blame).

Another thing that is becoming more important in cybersecurity in general is digital signing. You can have Git sign your commit using your provate GPG keys. Which allows other users to verify that you were in fact the one who commited it using your public key. If you want to read mroe on how to do this read [here](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work). GitHub/GitLab also have implemented this in their online editor, look for GPG keys on your private settings for the online repo. 


### Branches/pointers
Think of a branch as a story line, each branch is a series of commits. One can create a new branch by splitting of from a branch. In reality Git is very clever when it comes to how it work. Under the hood Git is just storing a graph of commits and it references them with pointers. It puts them together to form what we call branches. Pointers (or branch names) are just pointing to a specific commit, so think of them as labels which can point anywhere and be reassigned. 

If this got too confusing think of branches as an alternate timeline you can change between.    

There are two main pointers that you must know of. `HEAD` and `master`.

#### HEAD
`HEAD` points to where you are currently looking at (official lingo is the commit that is checked out). This label can point to any commit. 

#### Master
`master` is just the default branch created but the software Git (you can add/remove more if you want later).    

You may be asking yourself, what about `main`?????? Well that is just Github's push to rename it. Worth noting, Git is not the same a Github. 

It is good practice to use the your default branch as the branch where you have working code. If you build a new feature, create a new branch first and work of that. If your new feature breaks your project, you always have something that runs. This tip is specially useful at work, where you may be expected to have something that always works. Once you are ready with the feature you can merge it back into your main branch. In bigger projects (like  Ubuntu for example), new features dont get merged into the `master` branch easily, they go from dev branches to release candidates to alpah, to beta and then to master (not very accurate names here but you get the point). 

### Git command help
If you need to know how to use a command within git or would like to explore more advanced features within a command, you can use the `--help` flag. 

a few examples:
```bash
git --help
git init --help
git add --help
git stash --help
```

If it pops you into a help entry that you dont know how to exit use `q` on your keybaord to exit, use arrow keys to navigate around.


### Create a repository
Before you can do anything with the repository youhave to create one, this procedure is called initializing a repo. Createing a reposity is done once. It creates the folder structure that is required to manage and store your repository. It creates the folder `.git` in the root of your project and it stores eveything reguarding your repositity, mess/delete this and you repo is toasted. If you ever want to backup your project dont forget to save the `.git` folder too. 

To create a repo: 
- navigate to the root folder of your project
- run `git init`


### Git status
`git status` dispay the state of you stagin area and the state of your working directory. Somewhere in this file I talk about tracked files, those are teh files that git will tell you about. If you ever feel like you dont know what is going on, use this command.

It tells you infotmation regarding:
- Current working directory
- Repository files
- Staging area, aka things you want to add to your next commit
- **What branch you are currently in**
   - Some shells tell you waht branch you are in, for example `zshell`+ `oh my zsh`
   - by default you will have no idea where you are at so use `git status`
- Status regarding your merge procedures
- What files git is not tracking for you in this current directoty
- Many more ....



### Checking out a branch
Checking out a branch maens just moving/swtiching to that branch. Note this changes your files, if you have uncommited work it will ask you to do something with them. Untracked files are not touched.    

Use this command to switch/check-out a branch:   
```
git checkout <branchName>
```
You can also checkout a commit using its commit hash. 

### Creating a branch
The `branch` command lets you manage branches, the `checkout` commands lets you move arround. Git is very flexible and some commands overlap. 

There are a few ways of creating a branch, you can either:
- create it and then switch to it
- switch to it, but if it doesnt exit create it

Important to note that branches are created from your current location/branch this means that you have to either have to checkout that branch or specify in the command. 

Create a branch using these command:
```bash
# first move to that branch 
git checkout <sourceBranch>

# create a new branch with the branch command
git branch newBranch
# move to the new branch
git checkout <newBranch>


# or you can smash the last two commands with one command
git checkout -b <newBranch>
```

You can also create branched from any commit. Either checkout the commit or specify using its hash.


#### Creating branch from another branch or commit hash
As an example if we wante to create a new branch from a develop branch `dev` without changing into `dev` first, you can run the following command:

```
git checkout -b newFeature123 dev
```

This short command is the same as if you were running:
```
git checkout dev
git branch newFeature123
git checkout newFeature123
```
You can also create branched from any commit. Either checkout the commit or specify using its hash.

### Staging files 
To stage a file use: 
```
git add <file_name>
```

You can use absolute or relative pathing, it can be a file or a folder. As long it is withing your repository folder. 

#### Commiting changes 
This is where we create that snapshop of your files.

Use:
```
git commit
```

to commit your changes. You can also stage all your tracked files and commit in one go:
```
git commit -a
```

Commiting will pop into your editor of choise, where you will have to add a commit message. After you have successfully saved and returned from your editor is that git will proced to make the commit. 

#### Abort commit
abort a commit by leaving the file without a commit message. Coments are denoted by the chareacter `#` at the beginning of the line. Comments will not be added to your commit message. Therefore if you abort you dont have to delete them. 

#### Commit mesages
A commit message is a way to tell yourself or anyone else in the future what this commit was all about.    

The fist line is the title of the commit, all other lines are the detailed drescription of the commit. Any comments (lines that start with `#`) are not icluded.

The title should be short and sweet while still showing what was done. Here are a few examples:

- `Fix bug #53`
- add feature xyz
- delete file, deprecated
- XYZ replaced with ABC
- Update ABC value to 123 becasue its cool

descriptions are optional.

Here is a good read about what to put in a commit message. [How to Write Good Commit Messages: A Practical Git Guide
](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/).

Here is shorthand notation for staging and commiting and adding a commit message all at one:
```
git commit -a -m "This is the commit message"
```

### Unstage a file
So 👉👈 you accidentally stagged a file? well its easy.   
The command for unstaging a file depends on the circumstances the file was added. Worry not, I myself dont know what command to use, BUT git tells you. Just use the `git status` command and it tells you exactly how to do it.
<!--
### About unwanted changes, commits and pushing 
Commits are snapshots of your data, created by taking the difrerences from previous commits. They can get tricky to fix them as future things depends on previous commits. Read below TODO link, for more infor abou it.-->

### Commit history/git log 
The log command show you your commit history. It gives you information about the commits. As with most commands, it has more options within itself to get more advenced info, check the `--help` page for more info. 

Run with:
```
git log
```

Press `q` to exit. Use arros to move around. 

#### Viewing graph

If you would like to view a visual representation of what your repository looks like then you can use the following 
##### Locally 
Use the following command:
```
git log --graph --oneline --decorate --all
```
Press `q` to exit. That is kind of hard to remember, lets make a shortcut/alias with the following commnad (do only once): 
```
git config --global alias.graph "log --graph --oneline --decorate --all"
```

now lets use our alias:
```
git graph
```

##### Remotelly 
In github:
- Navigate to the repo page
- Click on `insights`
- Click on `network`

In GitLab:
- Navigate to repo page
- Navigate to `Repository`>`Graph`


## Remote repositories
In the initial part of this tutorial you worked locally. In this section you will be working with remote repositories. Essentially, it is copying/syncing your local repository with a remote server, This allows multiple people to work on the code at once. Merge conflicts are managed locally. The default name for your first remote server ina repository is `origin`. Your local repository can point to multiple remote locations, for example, one can push code to a backup code server, a production server, a developemnt server ...etc.

### Most common providers
You can register for an account on their respective websites.

- Github
- Gitlab
- Bitbucket


### Terminology
| Term | Description|
|:--:|--|
|Pull| Retrieve a copy of remote files into your local repo|
|Clone| Makes a copy of a remote repo (lind of like download it). This repo is alrady a repo and its configured
|Merge| When you want to join to branches back into one|
|Remote| A server hosting your repository in a remote location, like github or gitlab 

### Configuring credentials 
Credentials allow you to authenticate with the foreign server as the remote server will not allow anyone to edit the code (just the authorized individuals) and if the code is provate it may not allow anyone to pull from the code.
There are two methods, one is using HTTPS, the other is using SSH. HTTPS is just using your username and password for the remote repo. SSH is just like SSH key authentication, you share your public key with the remote server and the system takes cares of auth using your keys.

HTTPS is easier, but you have to login eveytime authentication is required. Which is what we are going to use for this tutorial. SSH has more initial setup, but after that you can forget about it.

More info on SSH setup [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh).

### Adding a remote location 
By default you new repository will not have any information about remote reoisitories, you have to add that manually. So if you start a new project locally and want to push it remotelly you will have to tell your local repo where to push it to, same applies to pulling. Clonning already sets this up for you. 


To add a remote use:   
```
git remote add <remote_name> <remote_URI>  
```

Where remote name is whatever you want call it and the remote URI can be HTTP/HTTPS protocol or SSH links to the repo. 

For example to create a new repo, add a remote, and pull its contents:
``` 
mkdir kb
cd kb
git init
git remote add https://github.com/NevadaCyberClub/knowkedge-base.git
git pull
```
You can alternatively clone it:
```
git clone https://github.com/NevadaCyberClub/knowkedge-base.git
```


List your remotes in a local repo:
```
git remote -v 
```
If you run that command your remotes may be listed twice, it just means that it had direction, when you add one by default it adds them into push and pull directions for that particular remote name. This means that you can use certain name but also pull and push from diferen servers. Essentially you can configure anything.    


Note: having mutliple remotes is useful when having mutliple servers that do different things, for example when you have CI/CD pipelines where code gets automatically deployed, you push to github and it archives it, you push to a testing remote and it gets checked, you push to remote server dev repo and it puts it in a production server. 

### Note on some comands 
If we take a look at the following command we see that we are talking about the server `origin` and local branch `master`:   
```
git push origin master
````
This implies that the remote branch is also called `master`. In the event that the remote branch is named diffrent you can specify as follows:      
```bash
git push <remote_name> <localBranchName>:<remoteBranchName>
```

### Pulling, Fetching
You can pull changes from a remote, essentially syncing your local branch with your remote branch. This can lead to merge conflics which you would have to fix. They are fixed inteh same fashion as merges. 
```
git pull
```

Fetching is similar to pull. Fetch only pull metadata about the state of the projets but doesn not touch your files. Essentially it allows yo to know if you are behind or ahead a few commits (see branch tracking).

### Pushing 
Pushing similar to pulling but in the oposite direction, essentially you are sengin your commits to the remote server. 

To push your local branch to a branch on the remote server(with the same name on the remote)
```
git push <remote> <LocalbranchName>
```

To push to a remote branch with a differente name in the remote (full notation):
```
git push <remote> <localBranchName:<remoteBranchName>
```

The same way you can pull whenever you want, You can do multiple commits without sycing eveytime, just push whenever you think its appropate.
You can push to any branch you woud like, by default its the defaul set in your remote server, usually master. Sometimes in the remote server master is a protected branch, meaning you cant edit it directly, you have to push to another branch and merge it int eh remote server (usually via gui, or via termianal using the force flags). 

#### Branch tracking
Branch tracking is when you let your local git repo know that a particular local branch is certain remote branch from a particular remote server. This can allow you to not specify remote and branches when you are talking/working on a local branch, allows you to do things like `git push`, `git pull` withut having to specify `origin master` for example. 

The easient way yo set this tracking is on the first push for that particular branch. The first inital push you will set your local branch to track a remote branch with the `-u`/`--set-upstream`  flag. For example `git push -u origin master`. If you have already pushed you can use `git branch -u <remote> <branch>` comand to achieve the same without pushing)


NOTE: pushing a branch does not automatically push all other branches, only the current one. So if you want to push another one di it manyally, if you want to push all use the `--all` flag (like so `git push <REMOTE> --all`, where REMOTE is your remote). 

### Merging
Merging means combining two branches into one, for example you have `master` and `dev` which has a new feature you are ready to integrate. You would merge `dev` into `master`. After this `master` and `dev` becomes one. Note, the arrows on the picture point the other direction as they are showing a graph, but historically its the other way around.

![git merge graph](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSuNpUR0C_2jLlM3JmedHUXDmkoZABkWQI4q_tZR4kn2W1JQjvGbVMjR6qTMJLNnNRBJf8&usqp=CAU)   

Git can usually figure out how to do the merge all by itself but sometimes if changes are made to the sames files in differente way on each branch the it will not know what to do, AKA a merge comflic accurs. 

Merging is something that you should become confortable with, (here)[https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging] is a resource on that specifically.

In a nutshell, git merges in two ways. In fast forward motion, which means all it has to do is udate the pointer. let say `master` did not change, and `dev` forked from it and made changed. All it has to do is move the `master` pointer to where `dev` and callit good.      
A three-way merge means that the commits at the two branches look different than the commit where they split of, threfore it doesnt know what to do and you have to intervene manually and tell git what you want to do. Again look at teh resource listed above.


### Pull vs Fetching
`git fetch` is the command that tells your local git to retrieve the latest meta-data info from the original (yet doesn’t do any file transferring. It’s more like just checking to see if there are any changes available).

`git pull` on the other hand does that AND brings (copy) those changes from the remote repository." -[from here](https://www.freecodecamp.org/news/git-fetch-vs-pull/#:~:text=git%20fetch%20is%20the%20command,changes%20from%20the%20remote%20repository.)

### Forking vs Cloning
Cloning is just downloading the copy of the repo (remote) to your local machine, this includes all the repository files.

Forking refers to splitting off from the project. In online repos (like github) there is ownership, and sometimes you cant modify the repo because you dont have permissions, so if you want to modify something you have to make a full copy of it and change it in your own copy. You can later submit a pull request and have the two repositories merge, similar to branchin within a repo but for repositories. 

# When in doubt use this
Here is a tip Ive picked up over years of using Git. If you have no idea what is going on us this command to gain a sence of what is happening. 
```
git status
```
Seems silly but git tells you what to do. You got yourself into a merge and have no idea what to do? `git status`. Accidentally staged a file? `git status` will tell you the right command to use. 

#### About messing up & playing with it
If you made a mistake in your repo and you want to fix it, or are doing a risky maneuver with with git. you can backup your repo by doing a complete copy of the project folder, **including the `.git` folder**. You can try things and see what works and what doesnt. If you fixed your mistake then good, else you have a backup you can start from again (if you play with it again make a new backup). 

In general when it comes to git repos, the longer you wait to fix the problem, I.E. the more you propagate the problem:
- Mistake
- Stage/add mistake 
- Commit mistake
- Push mistake to remote serrver
- Commit more changes after mistake
- Push commits after mistake on remote branch
the more complicated it gets to revert it. So as a rule of thumb, the sooner you spot a mistake on anyhing (realting to code or git related like commit mesages etc) the better. Consider this, if you are working on a team, and you push something that needs to be ammended, now at any pint anyone can either work on that code and push new stuff on top of that (remember that we use a remote server as a central hub of truth of the project). As git works by taking differences, the more stuff you pile on the history the harder it makes it to rewrite history. If you can fix things before things gets pushed remotelly the better. This does not mean that you cant fix things, it just makes it easier. 

When it comes to fixing things, you wil always find your answer on Google, just Google "I did this on git... how do I undo it/fix it", bound to find an answer.


# Advanced reading 
## Git bisect
Read more about bisect in the [git bisect docs](https://git-scm.com/docs/git-bisect). If you have a bug but you dont know what commit introduced it, this command is you friend, it lets you try out branches and asks you if you see the problem. It helps you find it. This command can not only be sued for finding bugs but helps you loacate branches using any binary questions, at teh end of the day its binary search.

# Workshop
Why reinvent the wheel. Go [here](https://github.com/kuahyeow/git-workshop/blob/master/README.markdown) for a nice introductory workshop.

<!-- REPLACED BY ABOVE WorKSHOP
# Tasks
This tutorial give you the brackground knowledge on how git works and what commands to use in which scenerio

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


-->


# Resources 
Documentation should be your friend here. They have examples most of the time.    
- [Complete list of all commands](https://git-scm.com/docs)
- [Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- 
# Sources 
- [@nachobacanful](https://gitlab.com/ignaciochg)'s 🧠

# TODO 
- add something explaining local vs global configurations 
- add bout git ignore
