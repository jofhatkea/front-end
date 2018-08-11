# Terminal Cheatsheet
Mac users have an excellent terminal built in, Windows users should either use git-bash or the terminal in your editor

See this post for help configuring VS Code to use "bash"

[stackoverflow post](https://stackoverflow.com/questions/42606837/how-to-use-bash-on-windows-from-visual-studio-code-integrated-terminal)

## Requirements
### codecademy, the command line
https://www.codecademy.com/learn/learn-the-command-line 
part 1, 2 & optionally 3

## using the terminal, cheatsheet
 - Remember, TAB is your friend, it can autocomplete a lot of stuff
 - Arrow up / down goes through your history, so you don't have to type the same over and over
 
| command | explanation | examples |
---|---|---
`cd`|change directory | `cd` navigates to your home folder
`cd ..`|go up one level|N/A
`cd ../../`|go up two levels|`cd ../..` does the same
`cd /`|go to the root of the machine/server|N/A
`cd folder`|go to the specified folder|`cd dist/js`
`pwd`|Print working directory| Prints out where you are
`ls`|list files in dir|N/A
`ls -lah`|List all files in dir, including hidden| N/A
`rm file.ext`|delete a file| can be used with a wildcard `rm *.html`
`rm -rf folder`|delete a folder and all sub folders| Beware `rm -rf /` would try to delete everything on your computer
`mv old new`|move/rename a file or folder|`mv out dist`
`touch file.ext`|create a new file or change it's "last edited status"|N/A
`open file.ext`|open the file in the preferred program|N/A
`>`|"pipe" the content from the terminal into a file|`ls -lah > out.txt`
`cmd1 && cmd2`|run commands after each other|`touch .gitignore && open .gitignore`