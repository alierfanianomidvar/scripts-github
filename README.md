# scripts-github

GitHub cheat sheet

## SETUP

You must set a clear name to easier for your teammate to identify you

- Set up your name :

      git config --global user.name "[firstname lastname]"

  You must set a clear name to easier for your teammate to identify you

- Set up your email

      git config --global user.name "[email_addre]"

  Enter valid email address

## INIT

You must set a clear name tobe easier for your teammate to identify you

- Initialize :

        git init

The git init command creates a new Git repository. It can be used to convert an existing, versioned project to a Git
repository or initialize a new, empty repository. Most other Git commands are not available outside an initialized
repository, so this is usually the first command you'll run in a new project.

- Retrieve :

        git clone "[project-git-url]"

git clone is primarily used to point to an existing repo and make a clone or copy of that repo at in a new directory, at
another location. The original repository can be located on the local filesystem or on remote machine accessible
supported protocols. The git clone command copies an existing Git repository.

#### git clone vs git init

git init and git clone can be easily confused. At a high level, they can both be used to "initialize a new git
repository." However, git clone is dependent on git init. git clone is used to create a copy of an existing repository.
Internally, git clone first calls git init to create a new repository. It then copies the data from the existing
repository, and checks out a new set of working files.

## Saving changes

The classic expression of "saving" is similar to the Git term "committing".

- Add changes :

       git add "[file or . (to add all files) ]"

  The git add is a command, which adds changes in the working directory to the staging area.

- Commit changes :

        git commit -m “[descriptive message]”

  The git commit command saves all currently staged changes of the project. Commits are created to capture the current
  state of a project.Before running git commit command, git add command is used to promote changes to the project that
  will be then stored in a commit.

- Diff :

    1. diff of what is changed but not staged :

           git diff

    2. diff of what is staged but not yet committed :

           git diff --staged

  The git diff is a multi-function Git command, which is used to compare changes committed in Git. Particularly, with
  the help of this command you can take two input data sets and output the modifications between them.

  ex -> https://www.freecodecamp.org/news/git-diff-command/

## STASH

The git stash command shelves changes you have made to your working copy, so you can do another work or to change
branches, and then come back and re-apply them.

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

  The git commit command saves all currently staged changes of the project. Commits are created to capture the current
  state of a project.Before running git commit command, git add command is used to promote changes to the project that
  will be then stored in a commit.

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

## GIT Remote Repository

- To create a new connection with a remote repo:

        git remote <name> 'or' <url>

    - After this you can use the name in other command and no need for url.

- Fetches a specific <branch>, from the repo:

        git fetch <remote> <branch name>
    - In other word with this command you will retrieve the lasts changes on the branch but without merging them with
      your
      local system.
    - If you want to fetch all remotes, you don't need to put the branch name.
    - **Example : git fetch origin development, this command will fetch all the latest changes
      form remote branch of development in remote repository origin. After running this command you can
      inspect the changes using `git diff` or `git log` and merge them to your local branch.**


- To fetch and merge all changes in your local system:

      git pull <remote> <branch name>

## GIT DIFF

- To Show difference between working directory and last commit :

        git diff HEAD

- To Show difference between staged changes and last commit :

        git diff --cached

## History

- To display the commit history of a repository:

        git log
    - **Example :**

      commit a3d0c2f0c6c9b6b4d4f4ab6f884f6ca1b0e0c6f7<br>
      Author: John Doe <johndoe@example.com><br>
      Date:   Tue Mar 29 11:24:57 2022 -0700<br>
      `Add new feature to homepage`<br>
      commit 9e862f899c7a0a8a8c7b3d3f1c7a1f68e3a3a2d2<br>
      Author: Jane Smith <jane@example.com><br>
      Date:   Mon Mar 28 14:09:41 2022 -0700<br>
      `Fix bug in login form<br>`

    - `--<limit number>` : Limiting the number of commit we want to see.
    - `--oneline` : Condense each commit to a single line.
    - `--author= ”<pattern>”` : Searching base author of the commit.
    - `--grep=”<pattern>”` : Searching for commits with a commit message that matches.
    - `<since>..<until>` : Getting the commit base on the specific time.
    - `-- <file>` : Searching commits base of the folder they are in.
- log of all the actions that have been performed in the repository,
  including commits, merges, rebases, and other operations :

        git reflog

## Visualizing Code Changes

- To display the difference between the last commit and working directory:

        git diff HEAD

- TO display the difference between the last commit and staged changes:

        git diff --cached

## Undoing Changes and Managing Code Versions

To undo the changes you have made, there are several commands available, here some of them:

- Create new commit that undoes the changes made in a previous commit, then apply it to the current branch:

        git revert

- Remove <file> from the staging area, but leave the working directory unchanged.
  This upstages a file without overwriting any changes. You can choose to reset to a specific commit,
  or to undo all changes since a certain commit. This command modifies the commit history,
  so it should be used with caution:

        git reset
    - `<commit>` : Reset staging area to a specific commit

- Reset staging area to match the recent commit and keep the changes from the staging area and leave the working
  directory unchanged:

        git rest --soft

- Reset staging area and working director to the last commit and overwrite all the changes:

        git rest --hard

> If you change your mind after using Git Reset, you can still restore the previous state of your repository by using
> the Git Reflog command.

- For permanently delete untracked files from your working directory:

        git clean

    - Before using this command you can use 'git clean -n', this command only shows the list
      untracked files in your system. So it's better before using git clean, use this command.

## Streamlining Your Workflow

- Interactively rebase current branch onto <base>. Launches editor to enter commands for how each commit will
  be transferred to the new base:

        git rebase -i <base>

## Collaborating and Sharing Your Work with Ease

- Uploading local repository content to a remote repository:

        git push origin '<branch name>'

### QUESTIONS

- How to resolve conflicts when pushing changes to a remote repository?
    - Before pushing your changes, use the git fetch command to download any changes made in the remote
      repository since your last pull or fetch.
    - Use the git diff command to view the differences between your local branch and the remote branch.
      This will show you any conflicting changes that need to be resolved.
    - Use a text editor or Git tool to resolve the conflicts in the affected files.
      This may involve modifying the code to incorporate both sets of changes or choosing one set of changes over the
      other.
    - Use the git add command to add the resolved files to the staging area.
    - Use the git commit command to commit the changes with a message describing the changes
      you made to resolve the conflicts.
    - Use the git push command to push your changes to the remote repository. If there are no further conflicts,
      your changes will be uploaded to the remote repository.
    - If there are still conflicts, repeat the process of resolving conflicts,
      adding changes to the staging area, committing changes, and pushing changes until all conflicts are resolved.

