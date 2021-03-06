---
lang: ja
author:
  twitter: falworks_ja
logical_url: /use-ts-in-js.html
description: たとえ TypeScript でコードを書かなくても、あなたの p5.js のコードは TypeScript の恩恵を受けることができます。
---

# TypeScript の機能を JavaScript のコードで使う

[VS Code](https://code.visualstudio.com/) は、それ自体がデフォルトで [TypeScript](https://www.typescriptlang.org/) を強力にサポートしています。  
たとえ TypeScript を使わなくても、JavaScript コードを書くときにその恩恵を受けられます。


## 型宣言を使う

[@types/p5](https://www.npmjs.com/package/@types/p5) は p5.js 用の型宣言です。これは TypeScript を使いながら p5.js のスケッチを作るときに必要になるものです。

ですが、この型宣言は JavaScript でコードを書くときにも役に立ちます。p5.js のリファレンス、つまり各種関数などの説明が埋め込まれていて、それを利用できるのです。

### 準備

`package.json` が存在しない（これは Template P が該当する）場合は、まず以下を行います。

- [pnpm](https://pnpm.js.org/) を使っていない場合、スケッチのフォルダー内に `package.json` を新しく作ります。  
内容は空のオブジェクト `{}` でよいです。
- [Git](https://git-scm.com/) を使っていて、かつ `.gitignore` が存在しない場合、これもフォルダー内に作ります。  
そして一行、`node_modules/` を追加します。このディレクトリーを無視するためです。

### 使いかた

まず @types/p5 をインストールします。  
`npm install -D @types/p5` または `pnpm add -D @types/p5` です。

そして、スケッチのフォルダー内に `tsconfig.json` ファイルを新たに作ります。  
内容は次のようなかんじです。

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

これで、マウスホバーで p5.js の関数の情報が見られるし、コード補完も効くようになります。

<div class="custom-wrapper-50">
  <img
    src="../images/spacer.png"
    data-src="../images/screenshots/use-d-ts.png"
    alt="JSファイルで型宣言を使う"
    class="custom-wrapped" />
</div>

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

こうすると、下記のコードはエラーを出し、それはエディター上に表示されます。

```js
let someNumber = 42; // 数値で初期化
someNumber = "1984"; // その後、文字列を入れる（できません）
```

これはバグを予防するのにとても有効です。

そしてもちろん、このようなケースだけではありません。たとえば `Cannot read property ‘...’ of undefined` みたいなエラーで悩むことも減るでしょう。重要なのは、多くのエラーが、プログラムを実行しなくてもコードを書いた直後に発見できるというところです。

### より複雑な型

もっと複雑な型が必要になることもあるかもしれません。たとえば上述のコードのようなことを意図的に行いたい場合です。それにはいくつかの回避策があります。

1. 変数を初期化なしで宣言する。

    ```js
    let someNumberlike;
    someNumberlike = 42;
    someNumberlike = "1984";
    ```

    ここで `someNumberlike` は `any` 型として認識されます。これはあらゆる種類の値を許容します（そしてそれは理想的ではありません。 たとえ望んでいなくても、オブジェクトや関数など他のどんな値でも代入できてしまうからです）。

2. [JSDoc](https://jsdoc.app/) コメントを書く。

    ```js
    /**
     * @type {(number|boolean)}
     */
    let someNumberlike = 42;
    someNumberlike = "1984";
    ```

    こちらの方法のほうがよいでしょう。JSDoc では値の型を指定することができ、VS Code はそれを理解します。

ところで、TypeScript ではもっとシンプルに書けます。

```ts
let someNumberlike: number | string = 42; // 数値も文字列も使えるように宣言する
someNumberlike = "1984";
```

もし興味があれば、TypeScript でコードを書いてみるのもおすすめです。
