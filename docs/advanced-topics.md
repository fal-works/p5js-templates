---
description: Some information related to p5.js Templates for advanced users (or those who want to be).
---

# Advanced Topics

## Publish your sketch

There are several platforms where you can post and share your sketch, such as [p5.js Web Editor](https://editor.p5js.org/) or [OpenProcessing](https://www.openprocessing.org/).

If you use [Git](https://git-scm.com/) and store your code on GitHub, you can also publish your sketch with [GitHub Pages](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages).  
Create a `docs` directory, and save there `index.html` together with other files to be loaded (which some templates already do in the `dist` directory), and then set the `docs` directory to be published.

## Edit HTML file and improve performance

The Template PETR+ does both of the two below:

- Adding `defer` attribute to the [\<script\> tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)s enables the JavaScript files to be loaded asynchronously without blocking the HTML parser. Do not use `async` attribute because the order of execution is important in our case using p5.js.

- You may load `p5.min.js` instead of `p5.js`. This will improve the runtime performance for the following reasons:
    - This file is minified i.e. has smaller file size, so it loads faster.
    - It disables the [p5.js Friendly Error System](https://github.com/processing/p5.js/blob/main/contributor_docs/friendly_error_system.md).  

    By the way you may also minify your own code using a minifier tool like [terser](https://terser.org/).

## Node.js module resolution

If you separate your source code into multiple files (modules), sometimes you may want use `index.js` for treating any directory as a module.  
Like this:

```js
// src/my-module/index.js

export { something };
```

```js
// src/main.js

import { something } from "./my-module";
```

This is allowed in a Node.js style. So you have to install and use a Rollup plugin [@rollup/plugin-node-resolve](https://www.npmjs.com/package/@rollup/plugin-node-resolve) for bundling that code with Rollup.

And if you use TypeScript, you also have to add the following config in `tsconfig.json`:

```json
{
  "compilerOptions": {
    "moduleResolution": "node",
  }
}
```

## Improve the build process for development

Creative coding often involves editing the code over and over again to fine-tune the results. So, if you use [TypeScript](https://www.typescriptlang.org/) or [Rollup](https://rollupjs.org/) or anything else, it may be a little annoying to build the sketch manually and wait for seconds each time.

Here are some tips for doing this process automatically and/or efficiently. These might also be useful for live coding.

### TypeScript

If you use TypeScript without any module bundler like Rollup, try adding an npm scripts command in the `scripts` field of `package.json`.  
Like the below (you can freely rename `dev`):

```json
{
  "dev": "tsc --watch"
}
```

then run it with `npm run dev`.

- This will watch your `*.ts` files and automatically transpile them (i.e. convert to `*.js` files) each time you save one of them.
- You can stop watching with `Ctrl + C` or `command + C`.
- The watch mode of TypeScript also has another advantage: it works faster than simply running `tsc`.

### Rollup

If you use Rollup without TypeScript, try adding a command like the below:

```json
{
  "dev": "rollup --config --watch"
}
```

then run it with `npm run dev`.

This will watch your source code files and automatically bundle them (i.e. generate a single `*.js` file) each time you save one of them.

### TypeScript & Rollup

If you use both TypeScript and Rollup, it's a bit more complicated. There are several ways as follows:

- Install [tsc-watch](https://www.npmjs.com/package/tsc-watch) (`npm install -D tsc-watch` or `pnpm add -D tsc-watch`).  
Maybe this is the simplest way; what it does is just running `tsc --watch`, but it also enables you to specify any succeeding command, something like this:

    ```json
    {
      "dev": "tsc-watch --onSuccess \"npx rollup --config\""
    }
    ```

- Install and use a Rollup plugin for TypeScript. Either one:
    - [@rollup/plugin-typescript](https://www.npmjs.com/package/@rollup/plugin-typescript)
    - [rollup-plugin-typescript2](https://www.npmjs.com/package/rollup-plugin-typescript2)
- If you don't mind doing a lot of config, you may use [Babel](https://babeljs.io/) or something.
- If you're OK with Node.js asynchronous programming, you may write your program that calls the JavaScript API of TypeScript/Rollup, and invoke it from any file watcher like [chokidar](https://www.npmjs.com/package/chokidar).
- If speed is a priority, try [esbuild](https://esbuild.github.io/). This is super fast, but it will strip away almost all comments in your code.
