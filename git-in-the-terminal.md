# git in the terminal

## Cheatsheet
| action | command | notes |
---|---|---
add a file (stage) | `git add filename.ext` | 
add all changed files | `git add --all`| beware!
commit staged files | `git commit -m "my commit message"`| 
add and commit, one-liner | `git commit -am "my message"` | does NOT add new/untracked files
push commited to remote | `git push` |
status | `git status` | overview of staged files etc, **really** usefull
rm | `git rm filname` | remove a tracked file (and delete it) e.g `git rm main.js`
**branches** | |
list branches | `git branch -a` | 
checkout a branch | `git checkout branchname`| ex: `git checkout login`
merge branch | `git merge branchname` | standing on the branch you wish to merge in to, remember to checkout the new branch. ex: `git merge login`
"set upstream" | `git push --set-upstream origin branchname` | ex: `git push --set-upstream origin login`
**cloning / initializing** ||
clone a repository | `git clone repositoryname.git` | will create a local folder called 'repositoryname', pass ` .` to clone to an existing folder
setup a new repo locally | `git init`| 
**other** | |
list commits | `git log`| This one has **a lot of options**, but this is my favourite `git log --oneline --all --graph --decorate`

### .gitignore
There are lots of files we do not wish to push, like platform dependent files ($Thumbs.db, mac hidden files, node_modules etc). Furthermore, it's considered bad practice to push "build" folders and minified source code.

We can create a file called `.gitignore` in the root of our project to lidt those files
1. `touch .gitignore`
2. `open .gitignore` or open it in your editor
3. Add a line for each folder / file to exclude from git, e.g.
    * `node_modules/`
    * `build/`
    * `TODO.md`

So if you add the line `node_modules` git status will no longer show it as being changed/added when you do a `git status`

### git workflow
There's no fixed way to do it, but here's a rule-of-thumb-aproach
1. `git branch todays-tasks`
2. `git checkout todays-tasks`
3. do some coding
4. `git add newfile.ext`
5. `git commit -m "some message"`
6. goto 4
7. Something is working: `git push --set-upstream origin todays-tasks` (only done once?)
8. `git push` and goto 4
9. Everything is awesome: `git checkout master && git merge todays-tasks`

### merge conflicts
They are bound to happen, and one of the main reasons we use git

First up, two ways to merge
1. From github.com
With two branches pushed to github, go to "Pull requests", select "master" as base, and choose the branch you want to merge into master

Then follow the GUI / instructions

2. Manually / terminal /editor
Requires a bit more work, but it's oh so nice :-)

Once a conflict is encountered, open the file in VS Code (or WebStorm) and use the GUI to select the changes you like

### Setting up a project
In the terminal, navigate to the root of your project and initialize it as a git repository
1. `git init`
2. Create a `.gitignore` file and add files/folders we do not wish to track
3. Add files to git (now we can use --all). `git add --all``
4. and then commit the files: `git commit -m "Initial commit"``
5. Then we need to set up the remote repository (i.e. github.com)
    1. On github create a new repository
    2. The page you get gives us the needed instructions to "push an existing repository from the command line", something like:
    ```
    git remote add origin https://github.com/jofhatkea/himomdeleteme.git
    git push -u origin master
    ```
6. Paste the command in the terminal
7. Finally, we can push our files: `git push`
