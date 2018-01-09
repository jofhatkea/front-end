# The Terminal, NPM & git in the terminal
Mac users have an excellent terminal built in, Windows users should either use git-bash or the terminal in your editor
## Requirements
### codecademy, the command line
https://www.codecademy.com/learn/learn-the-command-line 
part 1, 2 & 3

## git in the terminal
| action | command | notes |
---|---|---
add a file (stage) | `git add filename.ext` | 
add all changed files | `git add --all`| beware!
commit staged files | `git commit -m "my commit message"`| 
add and commit, one-liner | `git commit -am "my message" | does NOT add new files
push commited to remote | `git push` |
list branches | `git branch -a` | 
checkout a branch | `git branch branchname`| ex: `git branch login``
clone a repository | `git clone repositoryname.git` | will create a local folder called 'repositoryname', pass ` .` to clone to an existing folder
setup a new repo locally | `git init`| 
status | `git status` | overview of staged files etc, *really* usefull

## transpiling
### pure babel
``` "purebabel": "babel index.js --presets babel-preset-env --out-dir distribution" ````
But that won't enable "require", we need a bundler
Enter webpack
## linting

