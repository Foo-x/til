# 同じタグのイメージをpullしなおす

一度pullしたイメージはキャッシュされる。  
latestタグやメジャーバージョンのみのタグなどが付いたイメージも同様で、自動的に更新されるわけではない。  
更新するには再度pullするか、ビルドや起動時にpullしなおすオプションを付ける必要がある。  
主なコマンドとオプションは以下の通り。

- `docker build --pull`
- `docker run --pull always`
- `docker compose build --pull`
- `docker compose up --pull always`
