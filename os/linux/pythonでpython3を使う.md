# pythonでpython3を使う

`python`コマンドは、デフォルトでは実行できなかったり、`python2`を指していたりする。  
`alias python=python3`とすることで対話シェルから実行する場合は解決するが、シェルスクリプトの中などでは反映されない。  
`~/.local/bin/`などにPATHを通しておいて、`ln -sf /usr/bin/python3 ~/.local/bin/python`を実行すればOK。
