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
**other** | |
list commits | `git log`| This one has **a lot of options**

### git workflow
There's no fixed way to do it, but here's a rule-of-thumb-aproach
1. `git branch todays-tasks`
2. `git checkout todays-tasks`
3. do some coding
4. `git add newfile.ext`
5. `git commit -m "some message"`
6. goto 4
7. Something is working: `git push --set-upstream origin todays-tasks`
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

## NPM
NPM is our package manager, it handles downloading / using JS libraries for us.

Two new kids on the block are Yarn & Turbo, they do exactly the same, but a re a bit more shiny. NPM is still the standard, we'll use that
### Requirements
Install [Node](https://nodejs.org/en/) which will also install NPM (you should probably choose the LTS version)


`npm install`
`npm install -g live-server`
svgo
pageres-cli
https://github.com/sindresorhus/pageres-cli
https://github.com/purifycss/purifycss
purifycss src/css/main.css src/css/bootstrap.css src/js/main.js --min --info --out src/dist/index.css
(læser filer ind fra venstre til højre)
"purify": "purifycss index.html  a.css b.css bootstrap.min.css --info --out dist.css" virker
"purify": "purifycss index.html  bootstrap.min.css a.css b.css  --info --out dist.css" ocverser enkelte styles i a.css
purify skal nok kun bruges på framework css? evt på en fil af gangen?
### setup NPM for the current project
`npm init`
This will give us a file called package.json. We can add scripts/commands to it, to automate our workflow.

show cat css/*.css > bundle.css
convert to npm script
npm run myfirstscript

"bundlecss": "cat a.css b.css > bundle.css"
`cat styles/*.css > out/bundle.css`

npm run ....
npm start, test, pre?
--save --save-dev
## transpiling
### pure babel
``` "purebabel": "babel index.js --presets babel-preset-env --out-dir distribution" ````
But that won't enable "require", we need a bundler
Enter webpack
## linting

