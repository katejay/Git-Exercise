
# Git Commands

There are many different ways to use Git. Git supports many command-line tools and graphical user interfaces. The Git command line is the only place where you can run all the Git commands.

The following set of commands will help you understand how to use Git via the command line.
## Linux Commands

- mkdir

    mkdir *`<<DirectoryName>>`*
    ```bash
    mkdir UiFrontEnd
    ```
    This command will help you to create new folder in your local system as **`UiFrontEnd`**

    -----

- ls
    
    ```bash
    ls
    ```
    This command will help you to list all folders in current directory

    -----

- open 

    open *`<<Path>>`*
    ```bash
    open /c/users/jayk/desktop/git
    ```
    This command will help you to open path through terminals

    -----

- pwd

    ```bash
    pwd
    ``` 
    output -> /c/users/jay
    
    This will show present working directory

    -----

- cd

    cd *`<<DirectoryName>>`*
    ```bash
    cd UiFrontEnd
    ```
    This command will help you to change directory by passing directory name along with cd


## Git Basic Commands

- clone

    git clone *`<<RepositoryURL>>`*
    ```bash
    git clone 
    ```
    This command will help you to clone remote repository (code) in your local system

    -----

- config

    ```bash
    git config --global user.name "Jay"
    git config --global user.email "testuser@qa.co"
    ```
    This command will help you to set config on the global level by using "--global" along with git config, so it will applicable for all future commits

    -----

- status 

    ```bash
    git status
    ```
    This command will help you to get the status of the current folder, such as Untracked files, etc

    -----

- add 

    git add *`<<FileName>>`*
    ```bash
    git add pom.xml
    ```
    This command will help you to add a file to **`Stage Area`** from the **`Working Directory`** by passing the file name along with add command

    -----
    
- add . 

    ```bash
    git add . 
    ```
    This command will help you to add all files to the Stage Area, with a single command instead of adding each file one by one.

    -----
    
- commit

    git commit -m *`<<commit message>>`*
    ```bash
    git commit -m "This is my first commit"
    ```
    This command will help you to commit the file to your local repository (stage to local Repository) by adding the message "-m"

    -----

- push 

    git push *`<<RepositoryReference>>`* *`<<BranchName>>`*
    ```bash
    git push origin master
    ```
    This command will help you to push the committed code under **`local repository`** to **`Remote Repository`**

    -----

- pull

    ```bash
    git pull
    ```
    This command will help you to pull the latest code in your local repository

    The Main difference in Clone and Pull :

    - **`Clone`** command we use at the beginning to setup local repository **`Initially - One time only`**, while
    - **`Pull`** command we use to pull the latest code in local repository from remote repository **`Everytime after Clone`**

    -----

- fetch 

    ```bash
    git fetch
    ``` 
    This command will help you to get all latest commit/code in your local repository, but it won't merge it to local branch you are working on, i.e **`Working Directory`**
    
    Where as in git pull all latest commit/code are directly merge it to local branch

    We can switch to local repository, if we use fetch command by passing BranchName along with origin keyword
    
    git checkout origin/*`<<BranchName>>`*
    ```bash
    git checkout origin/feature/profile
    git checkout feature/profile
    ```
    We can merge the local changes to working directory, as pull using merge command and branch name along with origin keyword
    ```bash
    git merge origin/feature/profile
    ```

    -----

- clean 

    ```bash
    git clean -f
    ```
    This command will help you to clean the working directory. i,e untracked file. Where as -f stand for **`forcefully`** clean
    
    This command applied on the working directory, not on the Stage Area.

    -----

- log

    ```bash
    git log
    ```
    This command will help you to fetch all commits logs related to respective repository

    -----

- reflog

    ```bash
    git reflog
    ```
    This command will help you to fetch detailed logs with respect to **`local repository`**!

#  Branching 

- branch

    ```bash
    git branch
    ```
    This command will tell you what branch currently you on

    -----

- create branch 

    git checkout -b *`<<BranchName>>`*
    ```bash
    git checkout -b feature/profile 
    ```
    This command will help you to create a new branch from your current branch, and also switch to this new branch automatically.
    
    Here **`feature/profile`** is a new branch.

    Note : -b is used in above command to create a new branch, if we didn't mention above command it will be used to switch branches.

    -----

- switch branch

    git checkout *`<<BranchName>>`*
    ```bash
    git checkout master
    ```
    This command will help you to switch between branch.


# Revert Changes (mix/soft/hard)

- reset 

    ```bash
    git reset
    ```
    This command will help you revert the latest changes made in Stage Area.
    
    So all new changes will be removed from **`Stage Area to Working Directory`**. (backward process)
   
    This is also called as **`Mixed/Default/Soft Reset Mode`**
    
    Opposite to git add *`<<FileName>>`*
    
    NOTE : No Content is lost, it just changed from one state to another state

    -----

- reset --soft

    ```bash
    git reset --soft HEAD~1
    ```
    This command will help you to revert the latest commit made in Repository Head
    
    So the latest commit will be removed from **`Repository Head to Stage Area`**. (backward process)
    
    This is also called as **`Soft Reset Mode`**

    Opposite to git commit -m "new commit message"

    `--soft` indicate Soft revert

    `HEAD~1` indicate revert/remove 1 commit from top

    `HEAD~2` indicate revert/remove 2 commits from top

    NOTE : No Content is lost, it just changed from one state to another state

    -----

- reset --hard

    ```bash
    git reset --hard HEAD~1
    ```
    This command will help you to revert/remove latest commit and changes made in Repository Head
   
    So the latest commit will be removed from **`Repository Head to Working Directory`**. (backward process)
    
    This is also called as **`Hard Reset Mode`**
    
    Opposite to git add *`<<FileName>>`* , and git commit -m "new commit message"
   
    `--hard` indicate hard reset
  
    `HEAD~1` indicate revert/remove 1 commit from top
  
    `HEAD~2` indicate revert/remove 2 commits from top
    
    NOTE : Content is lost!!!

    -----

- reset --hard CommitHashcode

    git reset --hard *`<<CommitHashcode>>`*
    ```bash
    git reset --hard 4b36eab80afd8fd7f339d0475705b9e04485502a
    ```
    This command will help to directly jump to any particular commit and remove all previous commits, without using `HEAD~1`/`HEAD~2`..so on

    -----

- revert (preserve log)

    git revert *`<<CommitHashReference>>`*
    ```bash
    git revert 9be7d71
    ```
    This command will help you to store the information for delete commit
    
    Basically Create new commit to Remove code from targeted commit, (Recommended over hard or soft reset command)


# Merge and Rebase

- merge 

    ```bash
    git merge master
    ```
    This command will help you to merge the latest master code in your current branch. i,e pull the latest code in your current branch.
    
    Make the branch up to date with the latest master code to avoid merge conflict.
    
    NOTE : before using this command, make sure to update your master branch. by switching to master and pull latest code and again switch to working branch
    - Step 1. git checkout master
    - Step 2. git pull
    - Step 3. git checkout feature/profile
    - Step 4. git merge master
    - Step 5. press i to switch to insert mode 
    - Step 6. add commit message 
    - Step 7. once it is done, press `ESC` then `:` colon, then `wq` and hit enter

    -----
    
- rebase 

    ```bash
    git rebase master
    ```
    This command will help you to merge the latest master code in your current branch but in linear format.
    
    Difference between Normal Merge and Rebase is, 
    - Rebase provide linear commit history, where in Normal Merge commits are shown in zig zag format
    - There is no extra commits in Rebase, and used to avoid extra merge commits
    
    NOTE : before using this command, make sure to update your master branch. by switching to master and pull latest code and again switch to working branch
    - Step 1. git checkout master
    - Step 2. git pull
    - Step 3. git checkout feature/profile
    - Step 4. git rebase master
    - Step 5. press i to switch to insert mode 
    - Step 6. add commit message 
    - Step 7. once it is done, press `ESC` then `:` colon, then `wq` and hit enter

    -----

- squash

    ```bash
    git rebase -i HEAD~2
    ```
    This command will help you to combine multiple commits in a single commit.
    
    -i stand for interactive rebase
    
    HEAD~2 represent latest 2 commits from the top
    
    Use **`pick`** and **`squash`** keywords to combine multiple commit
    
    where **`pick`** is used for first commit 
    
    for other commits we can use **`squash`**
    
    Note : Do rebase first, then perform squash (combine multiple commits) !!!

    -----

- amend 

    ```bash
    git commit --amend
    ```
    This command will help you to push pending changes to latest commit

    If you forgot to add a file in commit. (Edit last commit by adding new files)

    -----

- amend with commit message

    git commit --amend -m *`<<NewCommitMessage>>`*
    ```bash
    git commit --amend -m "This is the new commit message"
    ```
    This command will help to Change/Edit the last commit message.
    
    -----

- show 

    ```bash
    git show
    ```
    This command will help you to show all files/changes you have in last commit

    -----

- cherrypick

    ```bash
    git cherry-pick 4b36eab80afd8fd7f339d0475705b9e04485502a
    ```
    This command will help you to share commit between branch
    
    For example we have to branch X and Y, if we want to share 1 commit from X to Y
    
    We can copy commit HashCode from branch X and use cherry-pick in Y branch 

    -----

- troubleshoot

    git checkout *`<<CommitHashReference>>`*
    ```bash
    git checkout 9be7d71
    ```
    This command will help you to travel to any commit by passing HashReference of commits
    
    Note : This feature is allow only to troubleshoot the problem, updating is not possible as HEAD is detach
    
    If we want to update any code, 
    
    - we need to create a new commit. OR 
    - we can cut the branch by creating a new branch and update that branch with new code and master code by using cherry-pick.


# Bisect 

- bisect

    ```bash
    git bisect start
    git bisect bad 9be7d71
    git bisect good 4b36eab
    git bisect bad 
    git bisect good
    ```
    This command will help you find the bad commit, this command usually performs when an application is failed.

    -----

- bisect reset

    ```bash
    git bisect reset
    ```
    This command will help you to get out side of bisect, and update the HEAD


# Stash

- stash

    ```bash
    git stash
    ```
    This command will help you to move your code in **`Saved Working Directory`** from **`Current Working Directory`**, without doing a commit. if we need to switch to any other branch without messed up code

    -----

- stash pop

    ```bash
    git stash pop
    ```
    This command will help you to retrieve all saved code from **`Saved Working Directory`** to **`Current Working Directory`**.

    -----

- diff

    ```bash
    git diff
    ```
    This command will help you to get content change in file

# Blame 

- blame 

    git blame *`<<FileName>>`*
    ```bash
    git blame test/sort.java
    ```
    This command will help you to get detailed information about the file, who wrote the code and time, etc.


# Tagging

- create tag 

    git tag *`<<TagName>>`*
    ```bash
    git tag v2.0 december-release
    ```
    This command will help you to create new tag, so you can attach it with latest commit

    -----

- create tag with message 

    git tag -a *`<<TagName>>`* -m *`<<Message>>`*
    ```bash
    git tag -a v2.0 december-release -m "Released hide profile feature"
    ```
    This command will help you to create a new tag with message, so you can attach it with latest commit

    -----

- get all tags

    ```bash
    git tag
    ```
    This command will help you to get all available tags

    -----

- push tags 

    ```bash
    git push --tags
    ```
    This command will help you to push all tags to commits

    -----
    
- push tag for perticular commit
    git tag *`<<TagName>>`* *`<<CommitHashReference>>`*
    ```bash
    git tag v1.0 november-release 4b36eab
    ```
    This command will help you to create a new tag for older or any specific commits by passing commit hash reference

