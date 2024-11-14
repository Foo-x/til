# sudoでPATHを引き継ぐ

普通にsudoでコマンドを実行すると現在のユーザのPATHが引き継がれない。  
`sudo env "PATH=$PATH" <command>` のようにすると引き継がれる。
