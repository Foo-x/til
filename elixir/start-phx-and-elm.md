# Phoenix + Elmプロジェクトの始め方

## 前提
- elixir, elmインストール済み
- `root/`はプロジェクトのルート

## 手順
1. `$ mix phx.new project-name`
  - デフォルトのデータベースはpostgresqlなので、mysqlに変える場合は`$ mix phx.new project-name --database mysql`
2. `root/config/dev.exs`, `root/config/test.exs`の最下段にあるRepoを設定
  - 使用するユーザはDBにあらかじめ作っておく
3. `$ mix ecto.create`
4. `$ cd root/assets`
5. `$ npm install --save-dev elm-brunch`
6. `assets/brunch-config.js`に以下を設定
  - `paths.watched`に`"elm"`追加
  - `plugins`に以下追加
    - `elmBrunch: { elmFolder: "elm", mainModules: ["src/Main.elm"], outputFolder: "../vendor" }`
7. `assets`以下に`elm/`ディレクトリ作成
8. `$ cd root/assets/elm`
9. `elm init`
10. `root/assets/elm/src/`以下に`Main.elm`ファイルを作成
  - 中は適宜実装
11. `root/assets/js/app.js`に以下を追記
  - `Elm.Main.init({ node: document.getElementById("elm-container") });`
12. `root/lib/projectname_web/templates/layout/app.html.eex`のbody内をcontainer.mainとscriptのみにする
13. `root/lib/projectname_web/templates/page/index.html.eex`を`<div id="elm-container"></div>`だけにする
14. `root/lib/projectname_web/router.ex`のscopeのgetを"/"から"/*path"にする
  - ルーティングをelmに任せる設定
