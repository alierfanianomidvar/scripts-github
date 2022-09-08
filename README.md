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
