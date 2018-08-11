# Setting up VS Code, part 2

## ESLint

"A pluggable and configurable linter tool for identifying and reporting on patterns in JavaScript. Maintain your code quality with ease."

Where Prettier was a plugin for formatting our code, ESLint is a plugin for analyzing our code and reporting on problematic places. Stuff like undeclared variables, varaibales that has been declared twice etc. Basically, this means we can discover problems with our JS before we execute it.

## First steps

First up, we need an NPM modules, so if you havn't already, we need to tell NPM we have a project.

1. `npm init`
2. And install eslint, `npm install --save-dev eslint`
3. Let's set up eslint: `npx eslint --init`
   - Yes, it says `npx`
4. Now we'll answer a few questions, the following are the best answers right now
   - "Use a popular style guide"
   - "Standard"
   - "JSON"
5. And finally, when it asks you to install a few packages, just say yes

This should create a new files called `.eslintrc.json` at the root of our project

When all of this is done, go ahead and install the eslint plugin to VS Code so everything works together.

`Cmd - Shift -X` to open the Extensions tab, and find the plugin called "ESLint", use the one by Dirk Baeumer.

## ESLint and Prettier, together

The final steps are a bit more complicated, but we have to make Prettier and ESlint work together (they both like to change the same stuff, and they do not agree on everything)

1. `npm install --save-dev eslint-config-prettier`
2. Add "prettier" to the `.eslintrc.json` file, so it looks like this:

```json
{
  "extends": ["standard", "prettier"]
}
```

Restart VS Code just in case.
Now you should have automatic formatting of code and the editor should highlight all parts of the code where it thinks there could be issues :-)

You can hover the highlighted parts to read what ESLint thinks the problem is

There are 100s of possibilities with both Prettier and ESLint, which is totally out of scope in this little tut, but take a look one day:
https://prettier.io/
https://eslint.org/
