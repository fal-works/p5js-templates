# Advanced Topics

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

- This will watch your source code files and automatically bundle them (i.e. generate a single `*.js` file) each time you save one of them.
- The `--config` option means that Rollup refers to the `rollup.config.js` file in your sketch folder.

### TypeScript & Rollup

If you use both TypeScript and Rollup, it's a bit more complicated. There are several ways as follows:

- Install [tsc-watch](https://www.npmjs.com/package/tsc-watch) (`npm install -D tsc-watch` or `pnpm add -D tsc-watch`).  
Maybe this is the simplest way; what it does is just running `tsc --watch`, but it also enables you to specify any succeeding command, something like this:

    ```json
    {
      "dev": "tsc-watch --onSuccess \"npx rollup --config\""
    }
    ```

- Install and use a Rollup plugin for TypeScript. Like [this](https://www.npmjs.com/package/@rollup/plugin-typescript) or [this](https://www.npmjs.com/package/rollup-plugin-typescript2).
- If you don't mind doing a lot of config, you may use [Babel](https://babeljs.io/) or something.
- If you're OK with Node.js asynchronous programming, you may write your program that calls the JavaScript API of TypeScript/Rollup, and invoke it from any file watcher like [chokidar](https://www.npmjs.com/package/chokidar).
- If speed is a priority, try [esbuild](https://esbuild.github.io/). This is super fast, but it will strip away almost all comments in your code.
