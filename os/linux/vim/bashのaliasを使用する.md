# bashのaliasを使用する

vim内から起動したシェルで.bashrcなどを読み込むには.vimrcに以下の設定を記載する。
(シェルに渡すオプション)

```
set shellcmdflag=-ic
```

ただし、この方法だとalias以外も読み込まれて、外部コマンド呼び出しが遅くなってしまう。  
したがって以下の方法をとると良い。

1. aliasのみを設定するファイルを用意
    - 非インタラクティブシェルではデフォルトでaliasを展開しないため、ファイルの先頭に `shopt -s expand_aliases` を記載して展開するようにする
2. .vimrcでそのファイルを読み込む設定を追加
    - `let $BASH_ENV="path/to/alias_file"`
    - `$BASH_ENV` は非インタラクティブシェルで読み込まれるファイル
