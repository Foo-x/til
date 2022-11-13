# 一部のみclone

## 結論

```sh
git clone --filter=blob:none --sparse <url>

cd <cloneしたディレクトリ>

git sparse-checkout set --cone path/to/target
```

git 2.34 以前は以下のようにする。

```sh
git clone --filter=blob:none --sparse <url>

cd <cloneしたディレクトリ>

git sparse-checkout init --cone

git sparse-checkout set path/to/target
```


## 補足

### ブロブレスクローン（パーシャルクローン）

`--filter=blob:none`

必要なファイルのみ実体をダウンロードする。  
過去のファイルはメタ情報だけ保持し、実体はダウンロードしない。  
checkoutやdiffをしたときにダウンロードされる。


### スパースチェックアウト

`--sparse`, `sparse-checkout`

指定したパスのファイルだけダウンロードする。  
`--sparse` でリポジトリのルートのみダウンロードし、`sparse-checkout` でパスを指定する。


## その他

### シャロークローン

`--depth 1`

指定した数だけ新しい順にコミットをダウンロードする。  
そのリポジトリのコマンドを使用したり、CIでテストしたりするなどで最新のコミットだけが必要なときに使う。  
開発用にクローンするときは使わない。（参考のリンク先を参照）


### ブランチ指定

`--single-branch -b <ブランチ>`

指定したブランチだけダウンロードする。  
fetchもそのブランチだけが対象になる。  
`-b <ブランチ>` を省略するとデフォルトブランチが対象になる。

あとで他のブランチも対象にしたいときは `.git/config` に `remote.fetch` を追加する。  
すべてのブランチを対象にしたいときは既存の `remote.fetch` のブランチ名を `*` にする。


## 参考

- [パーシャルクローンとシャロークローンを活用しよう - GitHubブログ](https://github.blog/jp/2021-01-13-get-up-to-speed-with-partial-clone-and-shallow-clone/)
    - シャロークローンが非推奨である理由あり
- [大きなGitリポジトリをクローンするときの工夫を図解します - DeNA Testing Blog](https://swet.dena.com/entry/2021/07/12/120000)
    - 毎回クローンするCIの場合はシャロークローンしてもOK
        - ただしJenkinsは一度クローンしたものに追加していくのでNG
- [git2.27以降にgit sparse-checkoutを使う場合はno-checkoutではなくsparseを使おう - はんなりと、ゆるやかに](https://iucstscui.hatenablog.com/entry/2020/08/29/080322)
