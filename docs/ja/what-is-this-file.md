# なんだこのファイル

[> Home](./)

## `.vscode` directory

このディレクトリーには、[VS Code](https://code.visualstudio.com/) 向けの設定情報が入っています。

- 編集中のコードを保存するたび、Prettier がコードを整形し ESLint が一部のエラーを修正します。これの自動実行を可能にしているのは `.vscode/settings.json` です。これとは別に、あなたの全プロジェクトに共通するグローバルな設定を書く場所もあるのですが、ローカルなほうの設定（各プロジェクトの `.vscode` の中のやつ）が優先されます。  
ちなみに VS Code にもデフォルトのフォーマッターが備わっています。多くの場合 Prettier のほうが有用だと思われますが、デフォルトのほうにしたくなるケースもあるかもしれません。

- `.vscode/tasks.json` は、`Ctrl + Shift + B` か `⇧⌘B` で呼び出されるデフォルトのビルドタスクを指定します。[ヒントとアドバイス](./tips.md)も参照。

### `LICENSE`

各テンプレートには `LICENSE` ファイルが入っていて、その内容は [Creative Commons Zero v1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)（略称 CC0-1.0）です。これは、そのテンプレートをコピペして使ってもよく、それに一切の制約が無いことを意味します。

関連のあるファイル：

- `package.json` ファイルにも `license` の項目があり、その値は `LICENSE` ファイルと一貫している必要があります。[package.json のドキュメント](https://docs.npmjs.com/cli/v6/configuring-npm/package-json) も見てみましょう。
- [Rollup](https://rollupjs.org/) を使うテンプレートでは、出力先のコードを生成するときにも `@license` タグを付与します（これは `rollup.config.js` ファイルのなかで設定されています）。

テンプレートを使ってスケッチを作り、それをコードも含めて公開したいときは……

- ご自分のコードを保護するためにはライセンスを削除するか、代わりに別のライセンスを付けるのもよいかもしれません。
- オープンソースライセンスというのがいくつか存在していて、CC0 は最も制約が緩いものの一つです。また、著作権について学ぶのにもちょっぴり時間が要るかもしれません。調べてみるとよいでしょう。

## `.gitignore`

`.gitignore` ファイルは、[Git](https://git-scm.com/) で無視する（管理対象外にする）ファイルを指定するためのものです。  

Git を使わない場合はこのファイルも不要です。

### `package.json`

このファイルは、`npm` あるいはその他のパッケージ管理ツールを使うのに必要です。これには、パッケージ間の依存関係の情報などといった各種メタデータが書かれています。

また、ユーザー定義のスクリプトが含まれていることもあります（「npm scripts」と呼ばれます）。これは `scripts` という項目で設定されていて、コマンドラインにて `npm run (コマンド名)` で実行できます。  
いくつかのテンプレートは、ブラウザーで動かすための JavaScript ファイルをビルド（生成）するために [TypeScript](https://www.typescriptlang.org/) や [Rollup](https://rollupjs.org/) を使います。このプロセスは自動化され、npm scripts でプログラムされています。

### `pnpm-lock.yaml`

このファイルは [pnpm](https://pnpm.js.org/)（[ヒントとアドバイス](./tips.md)も参照）によって生成されています。そのため、pnpm を使わない場合、このファイルは削除してよいです。  
依存パッケージをインストールするとき、デフォルトの `npm` は、代わりに `package-lock.json` を生成します。

これらロックファイルはたぶんあなたにとって重要ではないと思われますが、気になる人はググってみるのも良いでしょう。

### `style.css`

この CSS ファイルは `index.html` の表示のされ方を規定します。

各テンプレートの CSS ファイルは、margin/padding をなくして、さらにキャンバスに `display: block` を設定します。これは、ウィンドウ全体を使うようなスケッチを作るときに役に立ちます。

### `.eslintrc.json`

[ESLint](https://eslint.org/) のための設定です。

ESLint はいろいろな設定が可能で、[ここ](https://eslint.org/docs/rules/) で各種ルールの長大なリストを確認できます。

各テンプレートは、コード整形のために [Prettier](https://prettier.io/) を使い、ESLint のルールのうちコードの見た目にしか関係しないものは有効化しないように作られています。  
ただし、`lines-around-comment` ルールは有効化されています。Prettier がこのルールの動作をカバーしていないためです。残念ながら、このルールの [TypeScript](https://www.typescriptlang.org/) 版はこれを書いている時点では[存在していません](https://github.com/typescript-eslint/typescript-eslint/issues/1933)。

### `tsconfig.json`

[TypeScript](https://www.typescriptlang.org/) のための設定です。

このファイルは TypeScript のコンパイラーによって自動的に参照されます。

### `rollup.config.js`

[Rollup](https://rollupjs.org/) のための設定です。

`rollup` コマンドを実行するとき、`--config` オプションを与え、何もパスを与えないでおくと、Rollup は `rollup.config.js` を参照します。
