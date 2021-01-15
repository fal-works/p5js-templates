# Better coding experience

This is a set of GitHub template repositories for [p5.js](https://p5js.org/).  
Helps you write code and create sketches comfortably.

Assisted by several JavaScript development tools:

||Tool|What's that|
|-|-|-|
|P|[Prettier](https://prettier.io/)|Code formatter|
|E|[ESLint](https://eslint.org/)|Code linter|
|T|[TypeScript](https://www.typescriptlang.org/)|Typed JavaScript|
|R|[Rollup](https://rollupjs.org/)|Module bundler|

For the code editor, [VS Code](https://code.visualstudio.com/) is assumed to be used.


## List of templates

Choose one that suits your needs and preferences.

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


## More details

### Using [Git](https://git-scm.com/) and [GitHub](https://github.co.jp/)

- [Git](https://git-scm.com/) is a version control system, which will track changes to your code and do some other several jobs as well.  
And [GitHub](https://github.co.jp/) is an online platform for hosting code that are managed by Git.

- Git is useful but might also be a little difficult for programming beginners.  
Even if you don't use Git, you can still download each p5.js template from GitHub by clicking the "Code" button and then "Download ZIP".

- The `.gitignore` file is for specifying which files are to be ignored by Git.  
In case you don't use Git, you won't need that file as well.

- If you use Git and store your code on GitHub, you can also publish your sketch with [GitHub Pages](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages).  
Create a `docs` directory, and save there `index.html` together with other files to be loaded (which some templates already do in the `dist` directory), and then set the `docs` directory to be published.

### [VS Code](https://code.visualstudio.com/) configuration

- The `.vscode` directory contains configuration specific to VS Code.

- Running Prettier and ESLint automatically is enabeld by `.vscode/settings.json`. You might also have your own settings that globally apply to all of your projects, but the local ones will override the global ones.

- By the way VS Code has also its own default formatter. In many cases Prettier might be more useful but sometimes you might rather prefer the default one.

- Some templates require the command-line `npm run build` to be run for building the sketch (in our case, i.e. generating JavaScript files that can be run by browsers). Here you can use the shortcut keys `Ctrl`+`Shift`+`B` or `⇧⌘B` instead of manually typing and running the command. This is defined in the file `.vscode/tasks.json`.

### [npm](https://docs.npmjs.com/) related files

- [npm](https://docs.npmjs.com/) is a large database on the web, from which you can download several packages including the tools described above. It also provides a package manager tool (included in Node.js), which is a CLI (i.e. `npm` commands).

- The `package.json` file is necessary for using `npm` or other package managers. It contains several metadata (including package dependencies) and user-defined scripts as well (which are defined in the `scripts` field and can be run by command-line `npm run (script name)`).

- Instruction of each template (except for Template P) tells you to use the `npm` command, but it is also recommended to use [pnpm](https://pnpm.js.org/) instead (which is also used for developing these templates).

- If you don't use pnpm, you can ignore the file `pnpm-lock.yaml`. When installing dependencies, the default `npm` will generate `package-lock.json` instead. These lock files may not be important for you but google around it if you're curious.

- If something doesn't work, try reinstalling npm dependencies and then restarting VS Code.

### HTML/CSS

- Adding `defer` attribute to the [\<script\> tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)s enables the JavaScript files to be loaded asynchronously without blocking the HTML parser. Do not use `async` attribute because the order of execution is important in our case using p5.js.

- The CSS file in each template removes margin/padding and sets `display: block` for the canvas. This is useful if you create sketches that fit to the entire window.


## Developer's website

[FAL Works - https://www.fal-works.com/](https://www.fal-works.com/) - with a bunch of Processing/p5.js sketches.
