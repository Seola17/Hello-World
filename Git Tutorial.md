# Git and GitHub Tutorial For Beginners 2021
> 
> - Video link: https://www.youtube.com/watch?v=3fUbBnN_H2c
> - Markdown syntax guide: https://www.markdownguide.org/basic-syntax/
>
## How Git Works

* **Working Directory** (Local machine)  
    `git add`
  * Staging Area  
    `git commit`
  * Commit History  
  
    > each commit is a save point.  

    `git push`

* **Remote Server**  
    GitHub, Bitbucket, GitLab, ...
    with _git push & pull_, **collaboration** becomes handy!

## How to Initialize a Git Repository

> Repositories in Git contain a collection of files of various different versions of a project.

* to go to certain directory: `cd Desktop`
* to create a folder: `mkdir learning-git`
* to see the list of files: `ls`
* to make a directory a repository (to initialize): `git init .`

        Initialized empty Git repository in C:/Users/user/Desktop/learning-git/.git/  

    > We do this for a brand new project.  
    > Now we can issue git commands such as `git add`, `git commit`...

* to see the list of hidden items(.git): `ls -a`  

        ./  ../  .git/

* to delete the item(.git): `rm -rf .git`  
  
    > The tag `(master)`  is taken off the tail of the directory.  

        ~/Desktop/learning-git (master)
        ~/Desktop/learning-git

    > In current state, `git add` does not work, and it returns the error message:

        fatal: not a git repository (or any of the parent directories): .git

* to clean up the bash: `Ctrl + L`  


    > re-initialize the repository and re-try `git add` gives:

        Nothing specified, nothing added.


## Git Add
* to create a file: `touch index.html`, `touch index.js`, `touch main.css`
* to check the status of the git: `git status`

        On branch master

        No commits yet

        Untracked files:
            (use "git add <file>..." to include in what will be committed)
                index.html
                index.js
                main.css

        nothing added to commit but untracked files present (use "git add" to track)

* to get a file `index.html` tracked: `git add index.html`  

        On branch master

        No commits yet

        Changes to be committed:
            (use "git rm --cached <file>..." to unstage)
                new file:   index.html

        Untracked files:
            (use "git add <file>..." to include in what will be committed)
                index.js
                main.css

* to remove a file `index.html` from the staging area: `git rm --cached index.html`
  
    > It shows the original status, with nothing to commit and 3 untracked files.

* to add all the files from this current directory downwards: `git add .`

        On branch master

        No commits yet

        Changes to be committed:
            (use "git rm --cached <file>..." to unstage)
                new file:   index.html
                new file:   index.js
                new file:   main.css

* to remove all the files from the staging area: `git rm -r --cached .`
  
        rm 'index.html'
        rm 'index.js'
        rm 'main.css'

    > and it gives again the original status with nothing being tracked.  
    > we re-add all files with `git add .` to move on to the next step.