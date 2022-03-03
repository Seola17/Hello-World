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

* to create a folder: `mkdir test`  
* to change directory: `cd test`  
* to create a file: `touch test.js`  
  
        On branch master

        No commits yet

        Untracked files:
            (use "git add <file>..." to include in what will be committed)
                ../index.html
                ../index.js
                ../main.css
                ./

        nothing added to commit but untracked files present (use "git add" to track)

    > 4 files are being untracked.

* on the current directory `test`, if we do `git add .`:
  
        On branch master

        No commits yet

        Changes to be committed:
            (use "git rm --cached <file>..." to unstage)
                new file:   test.js

        Untracked files:
            (use "git add <file>..." to include in what will be committed)
                ../index.html
                ../index.js
                ../main.css

    > 3 files are still being untracked.  
    > Only `test.js` which was in the directory of `test` and _downwards_ was added.

* to add every file in any directory: `git add -A`
  
        On branch master

        No commits yet

        Changes to be committed:
        (use "git rm --cached <file>..." to unstage)
                new file:   ../index.html
                new file:   ../index.js
                new file:   ../main.css
                new file:   test.js

## Git Commit

> Commit is a **save point** before starting implementing another feature.

* to go back to the root directory (the upper folder): `cd ..`
  
        ~/desktop/learning-git/test (master)
        ~/desktop/learning-git (master)

* to issue a commit for all the 4 files in the staging area: `git commit -m "bootstrap project"`
  
        [master (root-commit) b8585e7] bootstrap project
        4 files changed, 0 insertions(+), 0 deletions(-)
        create mode 100644 index.html
        create mode 100644 index.js
        create mode 100644 main.css
        create mode 100644 test/test.js

    <!-- tsk -->

        $ git status
        On branch master
        nothing to commit, working tree clean

* to see the record of git activities: `git log`
  
        commit b8585e70a256068ae1575f1a1bbab3b88afb1e88 (HEAD -> master)
        Author: User <user@gmail.com>
        Date:   Thu Mar 3 21:05:58 2022 +0900

            bootstrap project

    > `b8585e70a256068ae1575f1a1bbab3b88afb1e88` is a unique commit **hash**.

* to see the information of a commit: `git show b8585e70a256068ae1575f1a1bbab3b88afb1e88`
  
        Author: User <user@gmail.com>
        Date:   Thu Mar 3 21:05:58 2022 +0900

            bootstrap project

        diff --git a/index.html b/index.html
        new file mode 100644
        index 0000000..e69de29
        diff --git a/index.js b/index.js
        new file mode 100644
        index 0000000..e69de29
        diff --git a/main.css b/main.css
        new file mode 100644
        index 0000000..e69de29
        diff --git a/test/test.js b/test/test.js
        new file mode 100644
        index 0000000..e69de29

* to open a file: `vi index.js`
* to edit: press `i` or `INSERT`
* insert: `console.log("hello git");`
* to quit: press `ALT + q` or `ESC`
* type: `:wq`
* to see the content of the file: `cat index.js`
  
        console.log("hello git");

    <!-- tsk -->

        $ git status
        On branch master
        Changes not staged for commit:
            (use "git add <file>..." to update what will be committed)
            (use "git restore <file>..." to discard changes in working directory)
                modified:   index.js

        no changes added to commit (use "git add" and/or "git commit -a")

* to see the change maded in current version with respect to the committed version: `git diff`
  
        diff --git a/index.js b/index.js
        index e69de29..8ed859e 100644
        --- a/index.js
        +++ b/index.js
        @@ -0,0 +1 @@

* to add this changement to the staging area: `git add .`
 
        $ git status
        On branch master
        Changes to be committed:
        (use "git restore --staged <file>..." to unstage)
                modified:   index.js

* to issue a commit: `git commit -m "added console.log"`
  
        [master 1945678] added console.log
        1 file changed, 1 insertion(+)

* to see the record on this repository: `git log`
  
        commit 19456789cc3c4f9c94a2596ed742a5779934a479 (HEAD -> master)
        Author: User <user@gmail.com>
        Date:   Thu Mar 3 21:27:09 2022 +0900

            added console.log

        commit b8585e70a256068ae1575f1a1bbab3b88afb1e88
        Author: User <user@gmail.com>
        Date:   Thu Mar 3 21:05:58 2022 +0900

            bootstrap project

* to see the commit information: `git show 19456789cc3c4f9c94a2596ed742a5779934a479`

        Author: User <user@gmail.com>
        Date:   Thu Mar 3 21:27:09 2022 +0900

            added console.log

        diff --git a/index.js b/index.js
        index e69de29..8ed859e 100644
        --- a/index.js
        +++ b/index.js
        @@ -0,0 +1 @@
        +console.log("hello git");

    > In the previous commit information, there was no + phrase, because we added an empty file.

* if we modify the file `index.js` again, this time removing the phrase we had added, `git diff` gives:
  
        diff --git a/index.js b/index.js
        index 8ed859e..8b13789 100644
        --- a/index.js
        +++ b/index.js
        @@ -1 +1 @@
        -console.log("hello git");
        
    > The deleted message is shown with - sign.

        $ git status
        On branch master
        Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
                modified:   index.js

        no changes added to commit (use "git add" and/or "git commit -a")

* to discard the change: `git restore index.js`
  
        $ git status
        On branch master
        nothing to commit, working tree clean

    > Now `git diff` does not give any result since there is no change with respect to the committed version.