# Setting up VS Code, part 3

## `eslint-plugin-compat`

Not all browsers are created equal. And some are old. Some browsers supports some stuff, and others, well, the support other stuff.

`eslint-plugin-compat` looks up our JS on caniuse.com and tells us, right in the editor, if we are using features/parts of the language, that is not supported in all browsers (like `fetch`)

## Install

`npm install --save-dev eslint-plugin-compat`

Then open the file `.eslintrc.json` and add the plugin to the "extends" section

`"extends": ["standard", "prettier", "plugin:compat/recommended"]`

Restart, just in case, and try typing `fetch("stuff") in to any JS file, it should warn us that this function is not supported everywhere... Awesome
