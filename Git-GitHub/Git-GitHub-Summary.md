# Git - GitHub
Before you start using Git, you have to make it available on your computer. Even if it’s already installed, it’s probably a good idea to update to the latest version. You can either install it as a package or via another installer, or download the source code and compile it yourself.

- Let's check if you have git in your computer.

`git --version`

- Installing Git

```https://git-scm.com/book/en/v2/Getting-Started-Installing-Git```

- Git needs your identity to mark/ label changes/ editor. 

```
- git config --list
- git config --global user.name "Fatih Tepe"
- git config --global user.email "fatihtepe@gmail.com"
- git config --global core.editor "vim"
```

## Create a local repo on your computer then push to Github

```
1. mkdir test   (on your terminal create a directory for example test)
2. cd test 
3. git init (or you can skip 1., 2., steps and directly write "git init test" (directory name)
4. git branch -m main (if your branch name is master change it to main if it is main, skip)
5. Create a repository on Github [https://github.com/](https://github.com/) (copy url address of your repo)
6. git remote add origin [git@github.com](mailto:git@github.com):fatihtepe/test.git  (remote repository github)
7. git pull origin main
8. here you can create as many as file you want then git add . ==> git commit -m 'message'
	if you want to change your message ==> git commit --amend -m "write your new message"
	""" After git add . ==> To Undo these command 

		1. git reset README.md (file name here it is README file) 

		To Undo Commit

		1. git reset HEAD~1 (HEAD point last commit go 1 back)"""

9. git push origin main 
10. Check your github account you will see your repo there
```
## Creating a Remote Repo on GitHub

```
1. Sign into https://github.com (give a name (for example 
	"creating_repoManual" this name will be directory name on your 
	computer , select initiating Add a README file, Public etc.)
2. Click 'Create repository' button
3. Copy https url address [https://github.com/fatihtepe/creating_repoManual.git]
	https://github.com/fatihtepe/creating_repoManual.git)
4. Open Terminal
5. cd  where you keep your git repos
6. git clone h[ttps://github.com/fatihtepe/creating_repoManual.git]
	(https://github.com/fatihtepe/creating_repoManual.git) 
	now we cloned your github repository to our working area
7. cd creating_repo Manual 
8. You don`t need to use git init to initiate a repo when you clone it from remote
9. git branch (before creating new new branch let's check where we are 
10. git branch manual (creating manual branch)
11. git checkout manual (we are now on manual branch)
12. git branch ( check again and see the new branch green colored)
13. touch repoManual.txt (creating a txt file etc.)
14. ls (here you will see [README.md] and repoManual.txt)
15. open repoManual.txt file and work on it..
15. cat repoManual.txt (you can check!) WORKING DIRECTORY
16. git status (you will see there red coloured file/s)
16. git add repoManual.txt ( or just dot . for all files, STAGING AREA)
17. git commit -m "Repository Manual for Beginners" (committing Local Repository)
18. git log (check your log)
19. git push origin manual (pushing branch to remote..we do not need to use 
	(git remote add origin) command because we cloned our repo 
	from remote and both are already associated with each other)
20. Let's go and check our github, remote, repo. We have two branch (main and manual)now. 
21. Compare & pull request (click here to open pull request you 
	will see there 'Able to merge' remark.your last commist message will be inserted automatically. 
	Click green coloured 'Create pull request'
22. Merge pull request (there you will see no conflict to merge and click Merge pull request)
23. Confirm merge
24. Pull request successfully merged and closed.
25. Click Code tab to see how the repo looks like after merge. 
	As you see manual branch is merged to the main branch.

### Final Notes! ###

	We have two branch in this example main and manual , a new branch 
	(manual) on our local repo and pushed it to remote repo. Now, our remote repo 
	(Github) is on main branch and up to date, but local repo is not. So,
	
First, switch to main branch

$ git checkout main

Then type

$ git pull origin main

GREAT!!

NOW 

Everything up-to-date
```
## How to fork a repo in GitHub

`Most of the time, people fork projects to propose 
	changes to someone else’s project.`

```
1. Find the repository you want to fork on GitHub on right corner, Click Fork
2. Then choose your github account now it is your repository
3. Copy the url from your account 
2. Open Terminal cd where you want to clone
3. git clone https://github.com/fatihtepe/python.git
4. cd (directory which you cloned/forked)
5. ls (to see files in directory)
7. git remote -v (see where you are)
6. git branch (see what branch/es you have)
7. git checkout -b newbranch (create and switch newbranch)
8. git status (you are on new branch and nothing to commit)
9. ls (to see files in directory(same files in main branch))
10. vim file (choose a file to make some changes)
11. git status
12. git add . (to stage changes dot for all files or you can write the file name)
13. git status (changes ready for committing)
14. git commit - m 'message' (commit file/s)
15  git status (working tree clean)
16. git remote -v (you will see your GitHub account we are still here)
17. git remote add upstream git@github.com:TylerCounter/python.git (this url is forked url not ours
	here we are checking to see wether any changes or not on the forked repo..remember normally we
	used 'git remote add origin' here this is others repo so we use upstream not origin here)			
18. git remote -v (now you will see origin repo address and upstream(forked) url here "verify the new 
	repository you've specified for your fork)
19. git pull upstream main (same here not origin we use upstream to see any changes)
20. git push -u origin newbranch 
21. open your GitHub account you will see there "compare & pull request" green lighted click it.
22. The pull request page is opened and you will see "Create pul request" green lighted write your
	request what you did to the owner of upstream repo) click it
23. Now my request was created. It will be checked by owner of upstream repo.
```

## A perfect Hands-on

```
1. Create a public repository in GitHub
2. Clone your remote repository to your computer (Open Terminal)
	-	mkdir directoryname
	-	cd directoryname
	-	git clone url...(copy from GitHub)
3. cd directory where you cloned your remote repo
4. git status (on branch main)
5. Create a file/s
	-	touch file.txt (touch file.txt)
	-	vim/nano file.txt (do your work there)
6. git status (untracked files)
7. stage it ==> git add . (or write file name/s)
8. git status (see your file/s is ready to commit)
9. git commit -m 'any message related to your work update use simple tense'
10. git status (see your commit there ready to push to remote repo)
11. See the commit history
	-	git log 
	-	git log --pretty=oneline
	-	git log --oneline
12. git push (send the changes to your remote repo)
13. Go to your GitHub account and see the changes
14. Create new file on your GitHub (ex: test.html)
15. Commit new file on GitHub
16. Check your GitHub you can see your all commits there.
17. Go to terminal 
18. git log (you will not see any changes yet)
20. git fetch (or skip 20, 21, 22, 23 go directly 24)
	-	this command tells your local git to retrieve the 
		latest meta-data info from the original (yet doesn't do 
		any file transferring. It's more like just checking to see 
		if there are any changes available)
21. git diff main origin/main 
	-	see changes in local repository 
22. git merge 
	-	Combine main and origin/main
23. ls -l (see all files )
24. git pull 
	-	brings (copy) those changes from the remote repository
25. ls -l (see all files)
26. git log --oneline (see latest log there[create test.html])
27. git branch newbranch (you are creating new banch named newbranch here) (see 29)
	-	See branches 
		- git branch (show local branchs)
		- git branch -r (show remote branches)
		- git branch -a (show all local and remote branches)
28. git checkout newbranch (or you can write (git switch newbranch))
29. git checkout -b newbranch (here you can create a newbranch and switch it)
	-	with this command you can skip 27 and 28 steps.
30. ls or/and git status 
	-	List the files and check the status of the working directory
31. Here you can make any changes on your file/s
	-	vim file.txt etc.
32. Repeat 6, 7, 8 , 9, 10, 11, 
33. We are still on newbranch ==> git checkout main
	-	Switch the main branch and see the content of the​ test.txt
	-	cat file.txt
	-	no changes yet
34. git merge newbranch (we merged newbranch with main branch)
	-	cat file.txt (see the changes)
35. git push (Send the changes to the remote repository)
36. Go and check the remote repository
37. Go to Terminal if you want you can delete newbranch (you need to checkout 
	if you are currenly in the branch you want ot remove)
	- 	git branch -d (newbranch)
	-	git branch -D (newbranch)
	### Note: The -d option is an alias for --delete, which only deletes 
	the branch if it has already been fully merged in its upstream branch. 
	You could also use -D, which is an alias for --delete --force, which deletes 
	the branch "irrespective of its merged status.###
```

`create a new branch`
```
git branch branchname
```

`switch to a branch`
```
git checkout branchname
```

`Delete a branch from local to remote`
```
git push origin :branchname
```
`Delete a branch on a local repo`
```
git branch -d branchname
```
`git alias (an example for git log)`
```
git config --global alias.lg "log --graph --decorate --oneline --all"
```


