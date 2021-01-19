# Better coding experience.

<p><a href="https://twitter.com/intent/tweet?url=https://fal-works.github.io/p5js-templates/&text=p5.js+Templates&hashtags=p5js" target="blank_"><strong>>> [ Tweet ]</strong></a></p>

**en** / [ja](./ja/)

<img src="./images/flowchart.png" alt="p5.js Templates flowchart image" title="p5.js Templates" width="640" height="320">

This is a set of GitHub template repositories for **[p5.js](https://p5js.org/)**.  
Helps you write code and create sketches comfortably.

Assisted by several JavaScript development tools:

||Tool|What's that|
|---|---|---|
|P|[Prettier](https://prettier.io/)|Code formatter|
|E|[ESLint](https://eslint.org/)|Code linter|
|T|[TypeScript](https://www.typescriptlang.org/)|Typed JavaScript|
|R|[Rollup](https://rollupjs.org/)|Module bundler|

However you don't necessarily have to use all of them (see the template list below).

For the code editor, [Visual Studio Code](https://code.visualstudio.com/) (or VS Code in short) is assumed to be used.

*Note:* These are not for complete beginners and assume that you know about the basics of JavaScript and p5.js. However you don't have to be an expert at all!


## List of templates

On your needs and preferences.

### [[ P ]](https://github.com/fal-works/p5js-template-p)

Everything is automatically beautiful. [Prettier](https://prettier.io/) formats your code.

### [[ PE ]](https://github.com/fal-works/p5js-template-pe)

Less bugs and more readability. [ESLint](https://eslint.org/) checks your code automatically.

### [[ PET ]](https://github.com/fal-works/p5js-template-pet)

Prevent wrong values. More code completion. Code documents itself. With [TypeScript](https://www.typescriptlang.org/).

### [[ PER ]](https://github.com/fal-works/p5js-template-per)

Structure your source code with multiple files. [Rollup](https://rollupjs.org/) will bundle them.

### [[ PETR ]](https://github.com/fal-works/p5js-template-petr)

Combination of the two above.

### [[ PETR+ ]](https://github.com/fal-works/p5js-template-petr-plus)

No more global pollution. [p5.js instance mode](https://github.com/processing/p5.js/wiki/Global-and-instance-mode).  
In addition: [terser](https://terser.org/) minifies your code for distribution.


----


## More details

You don't necessarily have to read all of these first, but if it helps.

### Using Git and GitHub

- [Git](https://git-scm.com/) is a version control system, which will track changes to your code and do some other several jobs as well.  
And [GitHub](https://github.co.jp/) is an online platform for hosting code that are managed by Git.

- Git is useful but might also be a little difficult for programming beginners.  
Even if you don't use Git, you can still download each p5.js template from GitHub by clicking the "Code" button and then "Download ZIP".

- The `.gitignore` file is for specifying which files are to be ignored by Git.  
In case you don't use Git, you won't need that file as well.

### VS Code configuration

- The `.vscode` directory contains configuration specific to [VS Code](https://code.visualstudio.com/).

- Each time you save the code you are editing, Prettier formats it and ESLint fixes some errors. This automatic behavior is enabled by `.vscode/settings.json`. You might also have your own settings that globally apply to all of your projects, but the local ones (in `.vscode` of each project) will override the global ones.

- By the way VS Code has also its own default formatter. In many cases Prettier might be more useful but sometimes you might rather prefer the default one.

- Some templates require the command-line `npm run build` to be run for building the sketch (see also "npm scripts" below). Here you can use the shortcut keys `Ctrl + Shift + B` or `⇧⌘B` instead of manually typing and running the command. This is defined in the file `.vscode/tasks.json`.

### npm related files

- [npm](https://docs.npmjs.com/) is a large database on the web, from which you can download several packages including the tools described above. It also provides a package manager tool (included in Node.js), which is a CLI (i.e. `npm` commands).

- The `package.json` file is necessary for using `npm` or other package managers. It contains several metadata including package dependencies. It may also contain some user-defined scripts (see also "npm scripts" below).

- Instruction of each template (except for Template P) tells you to use the `npm` command, but it is also recommended to use [pnpm](https://pnpm.js.org/) instead (which is also used for developing these templates).

- If you don't use pnpm, you can remove the file `pnpm-lock.yaml`. When installing dependencies, the default `npm` will generate `package-lock.json` instead. These lock files may not be important for you but google around it if you're curious.

- If something doesn't work related to npm packages, try the below:
    1. Reload the VS Code window (`Ctrl+P` or `⌘+P` -> type `reload window` then `ENTER`).
    2. If still not resolved, reinstall package dependencies (`npm install` or `pnpm install`), then reload the window again.

### npm scripts

- Some templates use [TypeScript](https://www.typescriptlang.org/) and/or [Rollup](https://rollupjs.org/) for building a JavaScript file to be run on browsers. This process is automated and programmed with npm scripts, which are defined in the `scripts` field in `package.json` and can be run with command-line `npm run (command name)`.

- For understanding how to construct npm scripts, you may want to google around "npm scripts" or "npm run-script" or something. And check out the below:
    - Difference between globally and locally installed packages
    - What the `node_modules` directory is
    - Connecting commands with `&` or `&&` (this enables you to run them in parallel/sequential)
    - `pre`/`post` prefix of commands
    - `npx` command

### HTML/CSS

- The CSS file in each template removes margin/padding and sets `display: block` for the canvas. This is useful if you create sketches that fit to the entire window.

- Some VS Code extensions for HTML:
    - With [open in browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser) you can open any HTML file directly from VS Code.
    - If you load any asset file (e.g. an image) in your sketch, simply opening the HTML file won't work well. You may want to open it with [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer). It also refreshes the page each time a change is made to the JavaScript file.

### ESLint config

- The `.eslintrc.json` file contains configuration information of [ESLint](https://eslint.org/).

- ESLint is highly configurable; [here](https://eslint.org/docs/rules/) you can see a long list of rules.

- Each template is designed to use [Prettier](https://prettier.io/) for formatting code and do not enable ESLint rules that only affect the appearance of the code.  
However, the `lines-around-comment` rule is enabled, because the behavior of this rule is not covered by Prettier. Unfortunately a [TypeScript](https://www.typescriptlang.org/) version of this rule [does not exist](https://github.com/typescript-eslint/typescript-eslint/issues/1933) at the time writing this.

### License

- Each template contains a `LICENSE` file, and its content is [Creative Commons Zero v1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) (CC0-1.0 in short). This means that you can copy and use the template without any restrictions.

- Templates using [Rollup](https://rollupjs.org/) also attach a `@license` tag when generating the output code (this is configured in the `rollup.config.js` file).

- If you create a sketch using one of these templates and want to publish it including the code:
    - You may want to remove the license (or attach another one instead) to protect your own code.
    - There are several open source licenses and CC0 is one of the least restrictive. It may also take a little time to learn about copyright; let's check them out.

### Advanced

Here are some more information for advanced users (or those who want to be):

- [Advanced Topics](./advanced-topics.md)

However this doesn't mean that the topics in this page are easy enough.  
Learning takes time.


----


## Links

- FAL Works - <https://www.fal-works.com/>

    The website of the developer of p5.js Templates. With a bunch of Processing/p5.js sketches.
