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
add and commit, one-liner | `git commit -am "my message"` | does NOT add new/untracked files
push commited to remote | `git push` |
status | `git status` | overview of staged files etc, **really** usefull
**branches** | |
list branches | `git branch -a` | 
checkout a branch | `git branch branchname`| ex: `git branch login``
merge branch | `git merge branchname` | standing on the branch you wish to merge in to, remember to checkout the new branch. ex: `git merge login`
"set upstream" | `git push --set-upstream origin branchname` | ex: `git push --set-upstream origin login`
**cloning / initializing** | |
clone a repository | `git clone repositoryname.git` | will create a local folder called 'repositoryname', pass ` .` to clone to an existing folder
setup a new repo locally | `git init`| 

### git workflow
There's no fixed way to do it, but here's a rule-of-thumb-aproach
1. `git branch todays-tasks`
2. `git checkout todays-tasks`
3. do some coding
4. `git add newfile.ext``
5. `git commit -m "some message"
6. goto 4
7. Something is working: `git push --set-upstream origin todays-tasks`
8. `git push` and goto 4
9. Everything is awesome: `git checkout master && git merge todays-tasks`

## NPM


## transpiling
### pure babel
``` "purebabel": "babel index.js --presets babel-preset-env --out-dir distribution" ````
But that won't enable "require", we need a bundler
Enter webpack
## linting

