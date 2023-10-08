# WSLと Docker CE の環境でDevcontainerを使う

以下の条件でDevcontainerを使おうとするとエラーになる。

- WSLに Docker CE がインストールされている
- Docker CE のデーモンが起動していて、WSL内ではdockerコマンドが使える
- Docker Desktop がインストールされたまま
- Docker Desktop を停止していて、Windows側ではdockerコマンドが使えない

上の条件だと、VSCode からWSLに接続した状態であってもDevcontainerの起動時にWindows側のDockerを見ようとしてエラーになる。  
このときは `settings.json` に `"dev.containers.executeInWSL": true` を追加すると解決する。

なお、Docker Desktop をアンインストールすれば上の設定をしなくてもWSL側のDockerを見るのでエラーにならない。  
ただ、2023/10/08 時点で `Dev Containers: Clone Repository in Named Container Volume...` からDevcontainerを使おうとすると、Docker Desktop がアンインストールされていてもWindows側のDockerを見ようとしてエラーになる。  
このときも `settings.json` に `"dev.containers.executeInWSL": true` を追加すると解決する。
