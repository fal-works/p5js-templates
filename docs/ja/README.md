# より良いコーディング体験を。

<p><a href="https://twitter.com/intent/tweet?url=https://fal-works.github.io/p5js-templates/ja/&text=p5.js+Templates&hashtags=p5js" target="blank_"><strong>>> [ Tweet ]</strong></a></p>

[en](../) / **ja**

<img src="../images/flowchart.png" alt="p5.js Templates flowchart image" title="p5.js Templates" width="640" height="320">

これは、**[p5.js](https://p5js.org/)** 用の GitHub テンプレートリポジトリーの集まりです。  
コードを書いてスケッチを作るのを快適にしてくれます。

次のように、いろいろな JavaScript 開発用ツールの助けを借りています。

||ツール|なにそれ|
|---|---|---|
|P|[Prettier](https://prettier.io/)|コードフォーマッター|
|E|[ESLint](https://eslint.org/)|リンター|
|T|[TypeScript](https://www.typescriptlang.org/)|型付き JavaScript|
|R|[Rollup](https://rollupjs.org/)|モジュールバンドラー|

とはいっても、すべてを使う必要があるわけではありません（下記テンプレートリスト参照）。

コードエディターとしては、[Visual Studio Code](https://code.visualstudio.com/)（略称 VS Code）の利用を想定しています。


## テンプレート一覧

状況と好みに応じてお好きに。

### [[ P ]](https://github.com/fal-works/p5js-template-p)

全てが自動的に美しくなります。[Prettier](https://prettier.io/) があなたのコードを整形します。

### [[ PE ]](https://github.com/fal-works/p5js-template-pe)

バグは少なく、可読性は高く。[ESLint](https://eslint.org/) があなたのコードをチェックします。

### [[ PET ]](https://github.com/fal-works/p5js-template-pet)

値の入れ間違い防止。より良いコード補完。コード自体がドキュメントに。そう、[TypeScript](https://www.typescriptlang.org/) ならね。

### [[ PER ]](https://github.com/fal-works/p5js-template-per)

ソースコードを複数のファイルに分けて構造化しましょう。[Rollup](https://rollupjs.org/) が最後にまとめてくれます。

### [[ PETR ]](https://github.com/fal-works/p5js-template-petr)

上の2つの組み合わせです。

### [[ PETR+ ]](https://github.com/fal-works/p5js-template-petr-plus)

脱・グローバル汚染。[p5.js インスタンスモード](https://github.com/processing/p5.js/wiki/Global-and-instance-mode) です。  
ついでに、[terser](https://terser.org/) で配布用のコードを圧縮します。


----


## さらなる詳細

### Git と GitHub

- [Git](https://git-scm.com/) とは、バージョン管理システム。コードの変更履歴を追跡したり、いろいろやってくれます。  
そして [GitHub](https://github.co.jp/) は、Git で管理されたコードを保管してくれるWeb上のプラットフォームです。

- Git は便利ですが、プログラミング初心者には少し難しいところがあるやもしれません。  
Git を使わない場合でも、p5.js テンプレートを GitHub からダウンロードすることは可能です。「Code」ボタン→「Download ZIP」をクリックしましょう。

- `.gitignore` ファイルは、Git で無視する（管理対象外にする）ファイルを指定するためのものです。  
Git を使わない場合はこのファイルも不要です。

- もし Git を使っていて、コードを GitHub に保管しているのなら、そのスケッチを [GitHub Pages](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages) で公開できます。  
`docs` ディレクトリーを作り、そこに `index.html` と、そのなかでロードする他のファイルを置きます（いくつかのテンプレートはすでに同じことをしていて、`dist` ディレクトリーがそれです）。そして、`docs` ディレクトリーを公開するよう設定しましょう。

### VS Code の設定

- `.vscode` ディレクトリーには、[VS Code](https://code.visualstudio.com/) 向けの設定情報が入っています。

- 編集中のコードを保存するたび、Prettier がコードを整形し ESLint が一部のエラーを修正します。これの自動実行を可能にしているのは `.vscode/settings.json` です。これとは別に、あなたの全プロジェクトに共通するグローバルな設定を書く場所もあるのですが、ローカルなほうの設定（各プロジェクトの `.vscode` の中のやつ）が優先されます。

- ちなみに VS Code にもデフォルトのフォーマッターが備わっています。多くの場合 Prettier のほうが有用だと思われますが、デフォルトのほうにしたくなるケースもあるかもしれません。

- いくつかのテンプレートでは、スケッチをビルドする（ここでは、ブラウザーで動かせる JavaScript ファイルを生成する）ために、コマンドラインで `npm run build` を実行する必要があります。  
このとき、手で書いて実行する代わりに、ショートカットキーの `Ctrl+Shift+B` か `⇧⌘B` を使うこともできます。これは `.vscode/tasks.json` のなかで定義されています。

### npm 関連のファイル

- [npm](https://docs.npmjs.com/) は、上で書いたツールを含め様々なパッケージをダウンロードできる、Web上の大きなデータベースです。同時に、パッケージ管理のツールも提供します（Node.js に含まれています）。そのツールというのは具体的には CLI、つまり `npm` コマンドです。

- `package.json` ファイルは、`npm` あるいはその他のパッケージ管理ツールを使うのに必要です。これには、パッケージ間の依存関係の情報などといった各種メタデータが書かれています。  
また、ユーザー定義のスクリプトが含まれていることもあります。`scripts` という項目で設定されていて、コマンドラインで `npm run (スクリプト名)` として実行できます。

- 各テンプレートの説明の中で、`npm` コマンドを使うよう書いてあるところがあります（Template P を除く）。このとき、代わりに [pnpm](https://pnpm.js.org/) を使うのもおすすめです。これらのテンプレートを作るときにも使われています。

- pnpm を使わない場合 `pnpm-lock.yaml` は消して大丈夫です。依存パッケージをインストールするとき、デフォルトの `npm` は、代わりに `package-lock.json` を生成します。これらロックファイルはたぶんあなたにとって重要ではないと思われますが、気になる人はググってみるのも良いでしょう。

- npm 関連で何かがうまく動かないときは、以下を試してみてください。
    1. VS Code のウィンドウをリロードする（`Ctrl+P` か `⌘+P` → `reload window` と入力して `ENTER`）
    2. まだダメなら、依存パッケージを再インストール（`npm install` か `pnpm install`）して、再度ウィンドウをリロード

### HTML/CSS

- 各テンプレートの CSS ファイルは、margin/padding をなくして、さらにキャンバスに `display: block` を設定します。これは、ウィンドウ全体を使うようなスケッチを作るときに役に立ちます。

- HTML 用の VS Code 拡張もいくつかあります。
    - [open in browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser) では、任意の HTML ファイルを VS Code から直接開くことができます。
    - スケッチのなかで何らかのアセットファイル（画像とか）をロードする場合、単純に HTML ファイルを開くだけだとうまく動きません。[Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) で開きましょう。これはさらに、JavaScript ファイルに変更が加えられるたびにページをリフレッシュしてくれます。

- [\<script\> タグ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) に `defer` 属性を追加すると、HTML パーサーを停止させずに JavaScript ファイルを非同期でロードできます。p5.js の本体とスケッチの実行順序が重要なため、`async` 属性は使わないようにしましょう。

### ESLint の設定

- `.eslintrc.json` ファイルには [ESLint](https://eslint.org/) の設定情報が書かれています。

- ESLint はいろいろな設定が可能で、[ここ](https://eslint.org/docs/rules/) で各種ルールの長大なリストを確認できます。

- 各テンプレートは、コード整形のために [Prettier](https://prettier.io/) を使い、ESLint のルールのうちコードの見た目にしか関係しないものは有効化しないように作られています。  
ただし、`lines-around-comment` ルールは有効化されています。Prettier がこのルールの動作をカバーしていないためです。残念ながら、このルールの [TypeScript](https://www.typescriptlang.org/) 版はこれを書いている時点では[存在していません](https://github.com/typescript-eslint/typescript-eslint/issues/1933)。

### ライセンス

- 各テンプレートには `LICENSE` ファイルが入っていて、その内容は [Creative Commons Zero v1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)（略称 CC0-1.0）です。これは、そのテンプレートをコピペして使ってもよく、それに一切の制約が無いことを意味します。

- テンプレートを使ってスケッチを作り、それをコードも含めて公開したいときは……
    - ご自分のコードを保護するためには `LICENSE` ファイルを削除するか、代わりに別のライセンスを付けるのもよいかもしれません。
    - オープンソースライセンスというのがいくつか存在していて、CC0 は最も制約が緩いものの一つです。また、著作権について学ぶのにもちょっぴり時間が要るかもしれません。調べてみるとよいでしょう。


----


## リンク

- FAL Works - <https://www.fal-works.com/>

    p5.js Templates の開発者のWebサイト。Processing や p5.js のスケッチもいろいろあります。

- JavaScript用語集 開発環境関連 - <https://zenn.dev/fal/articles/js-dev-env-glossary-jan-2021>

    各種用語やツールなどの解説記事です。
