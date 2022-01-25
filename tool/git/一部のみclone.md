# 一部のみclone

## 結論

```sh
git clone --filter=blob:none --sparse --depth=1 <url>

git sparse-checkout init --cone

git sparse-checkout set path/to/develop

# git 2.35 からはinitせずに set --cone path/to/develop のようにできる
```


## 補足

### ブロブレスクローン（パーシャルクローン）

`--filter=blob:none`

必要なファイルのみ実体をダウンロードする。  
過去のファイルはメタ情報だけ保持し、実体はダウンロードしない。  
checkoutやdiffをしたときにダウンロードされる。


### スパースチェックアウト

`--sparse`, `sparse-checkout`

必要なファイルだけダウンロードする。  
`--sparse` でリポジトリのルートのみダウンロードし、`sparse-checkout` で必要なファイルを指定する。


### シャロークローン

`--depth=1`

最新のコミットから必要な履歴だけダウンロードする。


## 参考

- [大きなGitリポジトリをクローンするときの工夫を図解します - DeNA Testing Blog](https://swet.dena.com/entry/2021/07/12/120000)
