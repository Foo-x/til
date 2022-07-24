# monorepoで型定義を共有する

monorepoの構築は [monorepoをworkspacesで管理する](./monorepo%E3%82%92workspaces%E3%81%A7%E7%AE%A1%E7%90%86%E3%81%99%E3%82%8B.md) を参照。

1. 共有する型定義を管理するパッケージを任意の名前で追加する
    - 以下は `packages/types` に追加したとする
2. 追加したパッケージのスコープを `types` にする
    - `package.json` の `name` を `@types/foo` などとする
3. `package.json` の `types` に型定義ファイルのパスを設定する
4. ルートで `npm install` を実行すると `node_modules/@types/foo` にシンボリックリンクが張られ、各パッケージで参照できるようになる

`tsconfig.json` は適宜設定する。
