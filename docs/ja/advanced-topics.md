# 上級者向けトピックス

## Node.js のモジュール解決

ソースコードを複数のファイル（モジュール）に分ける場合、`index.js` を置くことで当該ディレクトリーをモジュールとして扱いたいと思うことがあるかもしれません。  
次のようにです。

```js
// src/my-module/index.js

export { something };
```

```js
// src/main.js

import { something } from "./my-module";
```

これは Node.js のスタイルで可能になります。なので、このコードを Rollup で扱うためには、Rollup のプラグイン [@rollup/plugin-node-resolve](https://www.npmjs.com/package/@rollup/plugin-node-resolve) をインストールして使う必要があります。

また、TypeScript を使う場合は、次の設定を `tsconfig.json` に追加することも必要です。

```json
{
  "compilerOptions": {
    "moduleResolution": "node",
  }
}
```

## 開発用ビルドプロセスの改善

クリエイティブコーディングでは、何度もコードを編集して結果を微調整することが多いです。なので、[TypeScript](https://www.typescriptlang.org/) や [Rollup](https://rollupjs.org/) などを使う場合、スケッチを毎回ビルドしてそのたびに数秒待つのがちょっと面倒かもしれません。

ここには、そのプロセスを自動化・効率化するためのヒントを置いています。ライブコーディングなんかでも役に立つかもしれません。

### TypeScript

TypeScript を使いつつ Rollup などのモジュールバンドラーを使わない場合は、`package.json` のなかの `scripts` のところに、npmスクリプトを追加してみましょう。  
次のようにです（`dev` のところは好きな名前で構いません）。

```json
{
  "dev": "tsc --watch"
}
```

そうしたら `npm run dev` を実行します。

- これは、`*.ts` ファイルをウォッチ（監視）して、そのどれかが保存されるたびに、自動でトランスパイル（`*.js` ファイルへの変換）が行われます。
- `Ctrl + C` や `command + C` でウォッチを停止できます。
- TypeScript のウォッチモードには他にも利点があって、普通の `tsc` よりも高速に動作します。

### Rollup

Rollup を使い TypeScript は使わないという場合は、次のようなコマンドを追加してみましょう。

```json
{
  "dev": "rollup --config --watch"
}
```

そうしたら `npm run dev` を実行します。

- これはソースコードをウォッチして、そのどれかが保存されるたびに、自動でバンドル（単一の `*.js` ファイルの生成）が行われます。
- `--config` オプションは、Rollup がスケッチのフォルダーのなかにある `rollup.config.js` を参照することを意味します。

### TypeScript & Rollup

TypeScript と Rollup を両方使う場合、もう少し複雑です。次のようにいくつかの方法があります。

- [tsc-watch](https://www.npmjs.com/package/tsc-watch) をインストールする（`npm install -D tsc-watch` または `pnpm add -D tsc-watch`）。  
おそらくこれが一番シンプルです。これは単に `tsc --watch` を実行するだけですが、次のように、後続のコマンドも一緒に指定できるのです。

    ```json
    {
      "dev": "tsc-watch --onSuccess \"npx rollup --config\""
    }
    ```

- Rollup の TypeScript 用のプラグインをインストールして使います。[これ](https://www.npmjs.com/package/@rollup/plugin-typescript)とか[これ](https://www.npmjs.com/package/rollup-plugin-typescript2)とか。
- あれこれ設定するのが嫌じゃなければ、[Babel](https://babeljs.io/) か何かを使ったり。
- Node.js での非同期プログラミングができるなら、TypeScript/Rollup の JavaScript API を呼び出すような独自のプログラムを書いてしまって、[chokidar](https://www.npmjs.com/package/chokidar) などのファイルウォッチャーでそれを起動するという方法も。
- スピードが優先なら、[esbuild](https://esbuild.github.io/) を試してみます。これは超速いんですが、コード中のコメントのほとんどすべてを削除してしまいます。
