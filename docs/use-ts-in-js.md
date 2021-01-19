# Use TypeScript features in JavaScript code

[> Home](./)

[VS Code](https://code.visualstudio.com/) itself has strong support for [TypeScript](https://www.typescriptlang.org/) by default.  
And your JavaScript code can also benefit from it even if you don't use TypeScript.


## Use type declaration

[@types/p5](https://www.npmjs.com/package/@types/p5) a type declaration for p5.js. This is something you'll need if you create p5.js sketches with TypeScript.

However, this type declaration is useful for your JavaScript code as well.

### Prepare package.json

If you don't use [pnpm](https://pnpm.js.org/), and if `package.json` does not exist (this is the case for Template P), create a new one in your sketch folder.

For the content an empty object `{}` is enough.

### How to use

First, install @types/p5.  
Either `npm install -D @types/p5` or `pnpm add -D @types/p5`.

Then create a new `tsconfig.json` file in your sketch folder.  
The content should be something like this:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "target": "ES2015",
    "types": ["p5/global"],
    "noEmit": true
  }
}
```

Now you can see Hover Information for p5.js functions.

<img src="./images/screenshots/use-d-ts.png" alt="Use type declaration in JS files" title="Use type declaration in JS files" width="480" height="240">


## Do type checking

After you create a `tsconfig.json` file as shown above, you'll also be able to do type checking for your JavaScript code.

Try adding `checkJs` option in your `tsconfig.json`:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "checkJs": true,
    "target": "ES2015",
    "types": ["p5/global"],
    "noEmit": true
  }
}
```

Now the code below raises a type error, which is quite useful for preventing bugs.

```js
let someNumber = 42; // initialize with a number
someNumber = "1984"; // then assign a string (which fails)
```

However sometimes you might need some more complex types, e.g. if you want to do something like the code above intentionally. In that case using TypeScript is necessary. A TypeScript code that works successfully would be as follows:

```ts
let someNumberlike: number | string = 42; // declare to accept both number and string
someNumberlike = "1984"; // now you can also assign a string
```
