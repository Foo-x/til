# netrwでディレクトリのコピー

Netrwでディレクトリをコピーしようとすると、末尾スラッシュの有無でvimとNetrwのカレントディレクトリが違うという内容のエラーが出てコピーできないことがある。（再現手順は不明）  
その際は `:let g:netrw_localcopydircmd='cp -r'` を実行するとコピーできるようになる。
