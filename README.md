# scripts-github
github cheat sheet

## SETUP
You must set a clear name to more easier for your teammate to identify you

- setup your name : 

      git config --global user.name "[firstname lastname]"

  You must set a clear name to more easier for your teammate to identify you
  
- setup your email

      git config --global user.name "[email_addre]"

  Enter valid email address


## INIT 
You must set a clear name to more easier for your teammate to identify you

- Initialize : 

        git init
        
 The git init command creates a new Git repository. It can be used to convert an existing, unversioned project to a Git repository or initialize a new, empty repository.  Most other Git commands are not available outside of an initialized repository, so this is usually the first command you'll run in a new project.       
 
- Retrieve :

        git clone "[project-git-url]"
        
 git clone is primarily used to point to an existing repo and make a clone or copy of that repo at in a new directory, at another location. The original repository can be located on the local filesystem or on remote machine accessible supported protocols. The git clone command copies an existing Git repository.
 
 #### git clone vs git init
 
   git init and git clone can be easily confused. At a high level, they can both be used to "initialize a new git repository." However, git clone is dependent on git init. git clone is used to create a copy of an existing repository. Internally, git clone first calls git init to create a new repository. It then copies the data from the existing repository, and checks out a new set of working files.

## Saving changes

The classic expression of "saving" is similar to the Git term "committing".

- Add changes : 

       git add "[file or . (to add all files) ]"
        
     The git add is a command, which adds changes in the working directory to the staging area.      
 
- Commit changes :

        git commit -m “[descriptive message]”
  
    The git commit command saves all currently staged changes of the project. Commits are created to capture the current state of a project.Before running git commit command, git add command is used to promote changes to the project that will be then stored in a commit.
    
- Diff : 

    1. diff of what is changed but not staged : 

           git diff
            
    2. diff of what is staged but not yet commited : 

           git diff --staged
           
        
     The git diff is a multi-function Git command, which is used to compare changes committed in Git. Particularly, with the help of this command you can take two input data sets and output the modifications between them.      
      
     ex -> https://www.freecodecamp.org/news/git-diff-command/

## STASH

The git stash command shelves changes you have made to your working copy so you can do another work or to change branches, and then come back and re-apply them.

- Save modified and staged changes :

        git stash
- list stack-order of stashed file changes :

        git stash list
- write working from top of stash stack :

        git stash pop
- choose from stash stack to write working :

        git stash pop stash@{"the number of chosen place"}
        
- discard the changes from top of stash stack:

        git stash drop 
        
- discard the changes from chosen place of stash stack :
        
        git stash drop stash@{"the number of chosen place"}
        
- discard all the stashes:

        git stash clear         
        
    The git commit command saves all currently staged changes of the project. Commits are created to capture the current state of a project.Before running git commit command, git add command is used to promote changes to the project that will be then stored in a commit.    




## Undoing changes

To undo the changes you have made, there are several commands available, here some of them:

- Create new commit that undoes the changes made in a previous commit, then apply it to the current branch:

        git revert

- Remove <file> from the staging area, but leave the working directory unchanged.
This upstages a file without overwriting any changes. You can choose to reset to a specific commit, 
or to undo all changes since a certain commit. This command modifies the commit history, 
so it should be used with caution:
        
        git reset

- For permanently delete untracked files from your working directory: 
      
        git clean

  - Before using this command you can use 'git clean -n', this command only shows the list
  untracked files in your system. So its better before using  git clean, use this command. 



## GIT BRANCHES

In Git, a branch is a separate line of development that allows you to work on a feature or bug fix without affecting 
the main code base. Each branch represents a snapshot of the code at a particular point in time.

When you create a branch, you essentially create a copy of the code base that 
you can modify without affecting the main branch. You can switch between branches, merge branches, 
and delete branches as needed.

- For seeing the list of all branches:

        git branch
- Creating new branch and moving to new branch:

        git checkout -b <branch name>
- For switching between branches:

        git checkout
