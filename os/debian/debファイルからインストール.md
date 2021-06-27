# debファイルからインストール

普通に`sudo apt install ./foo.deb`でOK。  
なお、相対パスの`./`は必須。（`sudo apt install foo.deb`はNG）

検索すると`dpkg -i ./foo.deb`でインストールする方法が出てくるが、これは依存関係を解決しないので、場合によっては`sudo apt install -f`を別途実行する必要がある。

アンインストールするときは`sudo apt remove foo`。（`foo`はファイル名ではなくパッケージ名）
