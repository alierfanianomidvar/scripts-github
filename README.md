# scripts-github

GitHub cheat sheet

## SETUP

You must set a clear name to be easier for your teammate to identify you

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
supported protocols. The git clone command copies an existing Git repository.(git clone will create near exact copy ofentire repo).

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

           git diff --staged or git diff --cached


  The git diff is a multi-function Git command, which is used to compare changes committed in Git. Particularly, with
  the help of this command you can take two input data sets and output the modifications between them.

  ex -> https://www.freecodecamp.org/news/git-diff-command/

 - The difference between git diff --cached (or its synonym git diff --staged) and git diff lies in what changes they compare:

      - git diff without any arguments displays the changes between the working directory and the index (staging area). This shows what has been changed, but is not yet prepared to be committed.

      - git diff --cached or git diff --staged shows the difference between the staged changes (in the index) and the last commit. It shows what has been added to the staging area and is ready for the next commit compared to the last commit you made.

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
- For updation branch name:

        git branch -m <new-branch-name>        

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

- To mark specific points in the history:

  - A `git tag` is a mechanism in Git to mark specific points in a repository's history as important. Typically, this functionality is used to mark release points (v1.0, v2.0 and so on).

  - There are two types of tags in Git:

    1. **Lightweight Tags**: These are essentially bookmarks to a commit; a pointer to a specific commit. Lightweight tags are created with the absence of the `-a`, `-s`, or `-m` options and do not contain any extra information beyond the commit itself.

    2. **Annotated Tags**: These are stored as full objects in the Git database. They are checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). Annotated tags are created with the `-a` option and are meant for release while lightweight tags are more for private or temporary object labels.

   - Here's how you might create each type of tag:

      - **Lightweight Tag**: `git tag v1.0`
      - **Annotated Tag**: `git tag -a v1.0 -m "Release 1.0"`

Tags are not automatically transferred when you `git push`. You have to push tags to a remote repository explicitly with `git push origin <tagname>` or `git push --tags` to transfer all at once. Similarly, they have to be explicitly fetched with `git fetch --tags` from a remote repository.      

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

  - In other word the soft reset (git reset --soft) moves the current HEAD to the specified commit,
    but does not change the index or the working directory. This means that the changes from the commits that are "removed" are kept in the staging area, ready to be re-committed if necessary.

- Reset staging area and working director to the last commit and overwrite all the changes:

        git rest --hard
  - In the other word a hard reset (git reset --hard), on the other hand, moves the HEAD to the specified commit and also updates the index and working directory to match that commit.
    This effectively discards any changes in the staging area and working directory that were made after the commit you reset to.

> If you change your mind after using Git Reset, you can still restore the previous state of your repository by using
> the Git Reflog command.

- For permanently delete untracked files from your working directory:

        git clean

    - Before using this command you can use 'git clean -n', this command only shows the list
      untracked files in your system. So it's better before using git clean, use this command.

- If you want to change the last commit message in Git before pushing it, you can use the following command:

        git commit --amend -m "New commit message"


## Streamlining Your Workflow

- Interactively rebase current branch onto <base>. Launches editor to enter commands for how each commit will
  be transferred to the new base:

        git rebase -i <base>

## Collaborating and Sharing Your Work with Ease

- Uploading local repository content to a remote repository:

        git push origin '<branch name>'


## Git best practices

### Commit messages >

- `Concise and Specific`: Commit messages should be brief yet descriptive. Ideally, they should convey the purpose of the changes made.

- `Use the Imperative Mood`: Start the commit message with an imperative verb like "Add", "Fix", "Update", "Remove", etc. For example, "Fix bug in payment gateway" or "Add new API endpoint for user profiles".

- `Capitalize the First Letter`: Begin the commit message with a capitalized letter.

- `Do Not End with a Period`: Commit messages typically do not end with a period.

- `Include Context`: If applicable, include a ticket number or context (like a feature or module name) in the commit message.

- `Detailed Description (Optional)`: For complex changes, you may add a detailed description in the commit message after a blank line following the short description. This is optional but recommended for complex commits.

        git commit -m "normal commit part" -m "Deatiled description part"

## Branch Naming Conventions

- `Consistent Structure`: Decide on a structure and stick to it. Common structures include using prefixes such as feature/, bugfix/, hotfix/, or release/.

- `Short and Descriptive`: Branch names should be brief but descriptive. For example, feature/user-authentication, bugfix/login-error.

- `Use Hyphens to Separate Words`: Use hyphens instead of spaces or underscores. For example, refactor-checkout-process.

- `Include Issue or Ticket Numbers`: If you're using a ticketing system, include the issue or ticket number in the branch name. For example, feature/123-add-search-functionality.

- `Avoid Sensitive Words`: Do not use offensive or insensitive language in branch names.

- `Lowercase Letters`: Use lowercase letters for branch names to avoid case sensitivity issues.



## Git Hooks: Automation and Custom Scripts in Workflow Management

Git hooks are scripts that Git executes before or after events such as: `commit`, `push`, and `receive`. They're a powerful tool for customizing Git's internal behavior and triggering customizable actions at key points in the development life cycle.

Git hooks are placed in the `hooks` subdirectory of the `.git` directory in a repository. By default, Git provides several sample hooks in a new repository, all of which are named as `<hookname>.sample`. To activate a hook, you rename the appropriate `.sample` file by removing the `.sample` extension and ensure that the script is executable.

Here are some of the most commonly used Git hooks:

- `pre-commit`: Runs during `git commit`, before the commit message editor is fired up. It's typically used to run linters, code formatters, or other tools that could validate the snapshot of code that's about to be committed.
  
- `commit-msg`: Invoked after the commit message has been entered but before the commit is completed. It's commonly used to validate or format commit messages.
  
- `pre-push`: Executes during `git push`, after the remote refs have been updated but before any objects have been transferred. It can be used to run tests or any other pre-push checks.
  
- `pre-receive`: Runs on the server side before a push is accepted. It can be used to enforce project standards or to run tests.
  
- `post-receive`: Executes on the server after a push has been accepted. It's often used to update other systems or notify CI/CD to start builds.

Using Git hooks can greatly increase productivity and maintain code quality by automating checks and balances. However, because hooks are executed on the local machine, any automated checks that are necessary to maintain code quality in the repository should also be implemented in a continuous integration system, which doesn't rely on client-side hooks.

Hooks can be written in any scripting language that your system can execute. It's important to note that hooks are not copied when you clone a repository, as they are a part of the `.git` directory. This is a security measure to prevent arbitrary code execution when cloning a repository.


#### State dependent environment changes:
```Text
This involves changes that are dependent on the state of the environment or the system, which might not be practical or reliable to handle with a Git hook, especially since hooks are not designed to manage environment states and might not have the necessary context to perform such actions.
```
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
      
- How to add and push a empty folder on repository?
    - Create a .gitKeep inside the folder and after you can add and push the folder inside your repo.
 
- What will happen if commit not only one but few commits but i want to change the first one?
    - If you want to change a commit that is not the most recent commit in Git, you will need to perform an interactive rebase to rewrite the commit history. Here are the general steps to achieve this:

    - Open a terminal and navigate to the root directory of your Git repository.Use the following command to start an interactive rebase session:

            git rebase -i HEAD~n

    - Replace n with the number of commits you want to go back. For example, if you want to edit the first commit, use 1. This will open a text editor with a list of commits. In the text editor that appears, replace the word "pick" with "edit" (or just "e") for the commit you want to modify (in this case, it's the first one).Save and close the text editor.
    - Git will now replay the commits up to the one you want to edit and stop at that commit, allowing you to make changes.
    - Make the necessary changes to your files.
    - Stage the changes using git add:

            git add <your_modified_files>

    - Amend the commit with your changes:

            git commit --amend
        - This will open the text editor again. Update the commit message if needed, save, and close the text editor.

    - Continue the rebase:

            git rebase --continue
      
    - Git will apply the remaining commits on top of the modified one.
 


    

