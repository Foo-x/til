# diffモードでよく使うコマンド

`vimdiff foo bar` や `vim -d foo bar` のようにすると、ファイル `foo` と `bar` の差分を比較するモードでvimを起動する。  
また、vimを起動中に `:diffs[plit] {filename}` でファイル {filename} を開くと現在のバッファと新しく開いたバッファとで差分を比較するモードになる。

- `]c`
    - 次の差分にジャンプ
- `[c`
    - 前の差分にジャンプ
- `:[range]diffg[et] [bufspec]`
    - 現在のバッファの [range] にある差分を [bufspec] の内容で更新
    - [range] を省略した場合は現在の位置かその上の差分
    - [bufspec] はバッファ番号かバッファ名のパターン
    - diffモードのバッファが2つの場合に [bufspec] を省略した場合は、もう片方のバッファ
        - 3つ以上の場合はエラー
- `:[range]diffpu[t] [bufspec]`
    - [bufspec] の [range] にある差分を現在のバッファの内容で更新
    - [range] を省略した場合は現在の位置かその上の差分
    - [bufspec] はバッファ番号かバッファ名のパターン
    - diffモードのバッファが2つの場合に [bufspec] を省略した場合は、もう片方のバッファ
        - 3つ以上の場合はエラー
- `[count]do`
    - `:diffget [count]` と同様
- `[count]dp`
    - `:diffput [count]` と同様
