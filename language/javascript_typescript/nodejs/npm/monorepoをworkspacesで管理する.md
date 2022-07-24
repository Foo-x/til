# monorepoをworkspacesで管理する

プロジェクトルートに `npm init` などで `package.json` を作成している状態だとする。  
このときに `npm init -w packages/foo` を実行すると `packages/foo` にパッケージが作成される。  
また、ルートの `package.json` に以下の値が追加される。

```json
{
  "workspaces": [
    "packages/foo"
  ]
}
```

なお、`packages` 以下で複数のパッケージを管理するのであれば、`"packages/*"` にしておくと `package.json` が毎回変更されないで済む。


## Tips

- ルートのパッケージをnpmに公開することはないので、`package.json` に `"private": true` を追加しておくと良い
    - 各パッケージは適宜設定する
- linterやformatterなど、複数のパッケージから共通して使う `devDependencies` はルートにinstallしておけば各パッケージにinstallしないで済む
- `npm run test -w packages/foo` と実行すると、`packages/foo` で `npm run test` を実行できる
    - パッケージは複数指定可能
- `npm run test -ws --if-present` と実行すると、`npm run test` を実行できるすべてのパッケージで実行できる
