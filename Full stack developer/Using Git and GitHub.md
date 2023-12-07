Before getting to know Git, its is important to know about Version control system. This allows you to keep track of changes to your documents.
- It will be easy to recover older versions of document if you make a mistake
- Making collaboration with others is much easier

Therefore, Git comes to earth:
- It is free and open
- Distributed version control system
	- Tracks changes to content
	- Provides a central point for collaboration
- Accessible anywhere in the world. That means people can have a copy of project on their own computer. When they've made changes, they can sync their version to a remote server to share with everybody

GitHub is one of the most popular web-hosted services for Git repositories. Others include GitLab, BitBucket and Beanstalk.

**Terminology**
SSH protocol: is the method for secure remote login from one computer to another.
Repository: The folders of project that are set up for version control. A data structure that stores documents and source code.
Fork: Copy of repository
Pull request: The process used to request that someone reviews and approves your changes before they become final

**Basic Git Commands**
git clone: Installs the repository from GitHub to local machine
git init: initializing new repository
git add (-A): moving changes from the working directory to the staging area
git status: allows you to see the state your working directory and the staged snapshot of changes.
git commit (-a): takes you staged snapshot of changes and commits them to the project
git reset: undoes changes that you've made to the files in your working directory
git log: enables to browse previous changes to a project
git branch: creates an isolated environment within the repository to make changes
git checkout: lets you see and change existing branches
git merge: lets you put everything back together again
git switch: changes to the specified branch
git branch -d: deletes the specified branch
git remote add (origin) ( https://github.com/vafekt/kolejnet.git): interacting with the repository in GitHub (used for pushing code into the repository)
git push -u (origin) (master): pushing code to the repository on the Internet
gitk: shows the graphical result
git pull: when you have changes in remote repository but still do not update in the local repository. It is used to have update.
git request-pull: to create a summary of changes for upstream to pull
git-daemon: a repository administrator use to allow anonymous downloads from the repository
git fetch: transfers any changes from remote repository to the local one.
![[Pasted image 20231207225106.png]]
"origin" word means the shorthand for the remote repository's URL

**Exploring the repository**
![[Pasted image 20231207143820.png]]
Code: Including the code
Issues: List all items against the project (problems)
Pull requests: Part of mechanism to collaborate with others. I defines changes that are committed and ready for review before being merged into the main branch.
Project: all the tools for managing, sorting, planning, etc. your various projects.

**GitHub Branches**
Branches stores all files in GitHub.
The master branch stores the deployable code (by default). But you can use any branch as the main (deployable version) of the code.
When you need to change things, you will create a new branch (a copy of original branch)
How to create branch?
![[Pasted image 20231207162253.png]]
Example (also explaining merging branches):
- Starting from the common base
- The code is branched while new features are developed (for example, 2 guys developing 2 new features)
- Now, both branches are undergoing changes
- When the 2 streams of work are ready to merge, each branch's code is identified as a tip. Two tips are merged into a third (combined branch)
![[Pasted image 20231207162657.png]]
- When having a branch, we change the contents (code) of the file. After finishing, changes are saved by commit. We need to describe what we changed in the box. But it is not the final project.
![[Pasted image 20231207163253.png]]
- We need the Pull Request. It makes the proposed (committed) changes available for others review and use.
- Pull requests can target specific users.
- In the log files, there will be the record of approval of the merge (person who approved the merge of the change).
- Step: Click Pull request and select New pull request:
![[Pasted image 20231207163750.png]]
- Then select the new branch from the compare box
![[Pasted image 20231207163928.png]]

What we do is to make sure that the master branch should be the only deployed code (merging into the master branch). Developers can change source files in a branch but the changes are not released until:
- They are committed
- A pull command is issued
- The code is reviewed and approved
- The approved code is merged back into the master code
![[Pasted image 20231207164329.png]]

**Cloning and Forking projects**
Cloning creates a copy of a repository on your local machine
Forking allows you to modify or extend a project without affecting the original project
- Forking takes a copy of a GitHub repository to use it as the base for a new project
- You can submit changes back to the original repository
When to fork or clone?
- if you have access to a project repo, e.g., as part of a team developing a codebase collaboratively, you can clone the repo and synchronize changes from your local copy of the repo using pull and push.
- If, however, there is a public project that you want to contribute to but do not have write access to, or use a public project as a starting point for your own project, you can fork the project.
- The project that you fork from is referred to as the `upstream` project

3 roles in Git
- Developer
- Integrator: Receives changes made by others, reviews and responds to pull-requests
- Administrator: structures repository organization