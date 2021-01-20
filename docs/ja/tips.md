---
lang: ja
logical_url: /tips.html
---

# ヒントとアドバイス

## pnpm を使う

デフォルトの `npm` コマンドの代わりに、代わりに [pnpm](https://pnpm.js.org/) を使うのもおすすめです（「p5.js Templates」を作るときにも使われています）。

クリエイティブコーディングでは小さなプロジェクトをたくさん作ることが多く、その都度様々なパッケージの依存関係をインストールすることになるので、このツールは特に有用です。

依存パッケージのインストールの際、`npm` か `pnpm` のどちらかを一貫して使うよう注意してください。

## なにかがうまく行かないときは

次のことを試してみてください。

1. VS Code のウィンドウをリロードする（`Ctrl+P` か `⌘+P` → `reload window` と入力して `ENTER`）
2. まだダメなら、npm パッケージのインストールがうまくできていない可能性があります。
`npm install` か `pnpm install` で再インストールして、再度ウィンドウをリロードしてください。

## JSDocコメントを使う

JavaScript のコードを [VS Code](https://code.visualstudio.com/) で開くと、`/** ... */` というコメントは [JSDoc](https://jsdoc.app/) として認識されます。

詳細は VS Code のドキュメントを見てください。[JavaScript in Visual Studio Code](https://code.visualstudio.com/docs/languages/javascript) の、"JSDoc support" や "Hover information" のあたりです。

## VS Code のショートカットキー

- いくつかのテンプレートでは、スケッチをビルドするために、コマンドラインで `npm run build` を実行する必要があります。このとき、手で書いて実行する代わりに、ショートカットキーの `Ctrl + Shift + B` か `⇧⌘B` を使うこともできます。

- `Ctrl+P` か `⌘+P` でコマンドパレットを開くことで、VS Code のあらゆるコマンドを検索・実行することができます。

## VS Code の HTML 用拡張機能

[open in browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser) では、任意の HTML ファイルを VS Code から開くことができます。

スケッチのなかで何らかのアセットファイル（画像とか）をロードする場合、単純に HTML ファイルを開くだけだとうまく動きません。  
[Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) で開きましょう。これはさらに、JavaScript ファイルに変更が加えられるたびにページをリフレッシュしてくれます。

## npm scripts について

npm scripts の構成方法を知るためには、CLI（コマンドライン・インターフェース）の基本に加えて、"npm scripts" とか "npm run-script" とかでググるとよいでしょう。そして次のことをチェックしましょう。

- パッケージのグローバルインストールとローカルインストールの違い
- `node_modules` ディレクトリーとは何なのか
- コマンドを `&` や `&&` で繋げることについて（これで並列・直列実行ができます）
- コマンドの `pre`/`post` プレフィックス
- `npx` コマンド
