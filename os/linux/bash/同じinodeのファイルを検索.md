# 同じinodeのファイルを検索

`find "$(findmnt -o TARGET -cenT <ファイル>)" -mount -samefile <ファイル>`

ハードリンクされているファイルの一覧を探すのに便利。  
なお、`ls -l` のパーミッションの右にある数字がハードリンクの数。
