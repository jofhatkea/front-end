# Fixing NPM permissions on a Mac

The following is a condensed version of https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally where I edited the parts where previous students had the hardest time :-)

1. Back up your computer.
2. On the command line, in your home directory, create a directory for global installations:
 `mkdir ~/.npm-global`

3. Configure npm to use the new directory path:
`npm config set prefix '~/.npm-global'`
4. Create a new file and set a new "PATH"
`echo "export PATH=~/.npm-global/bin:$PATH" >> ~/.profile`
5. On the command line, update your system variables:
 `source ~/.profile`
6. To test your new configuration, install a package globally without using sudo:
 `npm install -g jshint`