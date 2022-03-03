# Git and GitHub Tutorial For Beginners 2021
* Video link: https://www.youtube.com/watch?v=3fUbBnN_H2c
* Markdown syntax guide: https://www.markdownguide.org/basic-syntax/

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

## Repository

> Repositories in Git contain a collection of files of various different versions of a project.

* to go to certain directory: `cd Desktop`
* to create a folder: `mkdir learning-git`
* to see the list of files: `ls`
* to make a directory a repository (to initialize): `git init .`

        Initialized empty Git repository in C:/Users/user/Desktop/learning-git/.git/  

    > We do this for a brand new project.
    > Now we can issue git commands such as `git add`, `git commit`...

* to see the list of hidden files: `ls -a`

    > Terminal shows `./  ../  .git/` now.
