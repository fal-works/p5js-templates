# p5.js Templates

Collection of template projects for creating [p5.js](https://p5js.org/) sketches.

Assisted by several tools. On your needs and preferences.

||tool|what's that|
|-|-|-|
|P|[Prettier](https://prettier.io/)|Code formatter|
|E|[ESLint](https://eslint.org/)|Code linter|
|T|[TypeScript](https://www.typescriptlang.org/)|Typed JavaScript|
|R|[Rollup](https://rollupjs.org/)|Module bundler|

For the code editor, [VS Code](https://code.visualstudio.com/) is assumed to be used.


## List of templates

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

### [npm](https://docs.npmjs.com/) related files

- [npm](https://docs.npmjs.com/) is a large database on the web, from which you can download several packages including the tools described above. It also provides a package manager tool (included in Node.js), which is a CLI (i.e. `npm` commands).

- The `package.json` file is necessary for using `npm` or other package managers. It contains several metadata (including package dependencies) and scripts (which can be run by `npm run (script name)`).

- Instruction of each template (except for Template P) tells you to use the `npm` command, but it is also recommended to use [pnpm](https://pnpm.js.org/) instead (which is also used for developing these templates).

- If you don't use pnpm, you can ignore the file `pnpm-lock.yaml`. When installing dependencies, the default `npm` will generate `package-lock.json` instead. These lock files may not be important for you but google around it if you're curious.

- If something doesn't work, try reinstalling npm dependencies and then restarting VS Code.

### Using [git](https://git-scm.com/)

- [git](https://git-scm.com/) is a version control system. It will track changes to your code and also does other several jobs.

- The `.gitignore` file is for specifying which files are to be ignored by git. In case you don't use git, you won't need that file as well.

- If you use git and store your code on [GitHub](https://github.co.jp/), you can also publish your sketch with [GitHub Pages](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages).  
For example, you can create a `docs` directory and save `index.html` there, together with other files to be loaded (which some templates already do with the `dist` directory), and then set the `docs` directory to be published.

### [VS Code](https://code.visualstudio.com/) configuration

- The `.vscode` directory contains configuration specific to VS Code.

- Running Prettier and ESLint automatically is enabeld by `.vscode/settings.json`. You might also have your own settings that globally apply to all of your projects, but the local ones will override the global ones.

- By the way VS Code has also its own default formatter. In many cases Prettier might be more useful but sometimes you might rather prefer the default one.

- Some templates require the command-line `npm run build` to be run for building the runnable sketch. Here you can use the shortcut keys `Ctrl`+`Shift`+`B` or `⇧⌘B` instead of manually typing and running the command. This is defined in the file `.vscode/tasks.json`.

### HTML/CSS

- Adding `defer` attribute to the [\<script\> tags](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) enables the JavaScript files to be loaded asynchronously without blocking the HTML parser. Do not use `async` attribute because the order is important in our case using p5.js.

- The CSS file in each template removes margin/padding and sets `display: block` for the canvas. This is useful if you create sketches that fit to the entire window.
