# Tips

[> Home](./)

## Using pnpm

Instead of using the default `npm` command, it is also recommended to use [pnpm](https://pnpm.js.org/) (which is also used for developing "p5.js Templates").

This tool is especially useful for creative coding, where you often create many small projects and install various package dependencies each time.

When installing package depencencies, be sure to run either `npm` or `pnpm` consistently.

## If something doens't work

Try the below:

1. Reload the VS Code window (`Ctrl+P` or `⌘+P` -> type `reload window` then `ENTER`).
2. If still not resolved, some npm packages may not be correctly installed.  
Reinstall them with `npm install` or `pnpm install`, then reload the window again.

## VS Code shortcut keys

- Some templates require the command-line `npm run build` to be run for building the sketch. Here you can use the shortcut keys `Ctrl + Shift + B` or `⇧⌘B` instead of manually typing and running the command.

- You can search and run any VS Code command by opening the command palette with `Ctrl+P` or `⌘+P`.

## VS Code extensions for HTML

With [open in browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser) you can open any HTML file from VS Code.

If you load any asset file (e.g. an image) in your sketch, simply opening the HTML file won't work well.  
You may want to open it with [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer). It also refreshes the page each time a change is made to the JavaScript file.

## About npm scripts

For understanding how to construct npm scripts, you may want to google around "npm scripts" or "npm run-script" or something, as well as the basic of CLI (command-line interface). And check out the below:

- Difference between globally and locally installed packages
- What the `node_modules` directory is
- Connecting commands with `&` or `&&` (this enables you to run them in parallel/sequential)
- `pre`/`post` prefix of commands
- `npx` command
