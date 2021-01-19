# TypeScript の機能を JavaScript のコードで使う

[> Home](./)

[VS Code](https://code.visualstudio.com/) は、それ自体がデフォルトで [TypeScript](https://www.typescriptlang.org/) を強力にサポートしています。  
たとえ TypeScript を使わなくても、JavaScript コードを書くときにその恩恵を受けられます。


## 型宣言を使う

[@types/p5](https://www.npmjs.com/package/@types/p5) は p5.js 用の型宣言です。これは TypeScript を使いながら p5.js のスケッチを作るときに必要になるものです。

ですが、この型宣言は JavaScript でコードを書くときにも役に立ちます。

次のようにして使ってみましょう。

1. [pnpm](https://pnpm.js.org/) を使っておらず、かつ `package.json` が存在しない（これは Template P が該当する）場合は、スケッチのフォルダー内に新しく作ります。その内容は空のオブジェクト `{}` でよいです。
2. `npm install -D @types/p5` か `pnpm add -D @types/p5` のようにして、@types/p5 をインストールします。
3. スケッチのフォルダー内に、`tsconfig.json` ファイルを新たに作ります。内容は次のような感じです。

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

これで、マウスホバーで p5.js の関数の情報が見られるようになります。

<img src="../images/screenshots/use-d-ts.png" alt="JSファイルで型宣言を使う" title="JSファイルで型宣言を使う" width="480" height="240">


## 型チェックを行う

上のようにして `tsconfig.json` を作ると、JavaScript コードに対して型チェックを行うこともできるようになります。

`tsconfig.json` に `checkJs` を足してみましょう。

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

こうすると、下記のコードはエラーを出します。これはバグを予防するのにとても有効です。

```js
let someNumber = 42; // 数値で初期化
someNumber = "1984"; // その後、文字列を入れる（できません）
```

しかし、もっと複雑な型が必要になることもあるかもしれません。例えば上のコードのようなことを意図的に行いたい場合です。そのようなケースでは TypeScript の利用が必要です。正常に動く TypeScript コードは、次のようなものになります。

```ts
let someNumberlike: number | string = 42; // 数値も文字列も使えるように宣言する
someNumberlike = "1984"; // これで文字列も代入できる
```
