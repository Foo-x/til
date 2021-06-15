# pythonでpython3を使う

`python`コマンドは、デフォルトでは実行できなかったり、`python2`を指していたりする。  
`alias python=python3`とすることで対話シェルから実行する場合は解決するが、シェルスクリプトの中などでは反映されない。  
`update-alternatives --install /usr/bin/python python /usr/bin/python3 100`を実行すればOK。  
上の設定を解除する場合は`update-alternatives --remove python /usr/bin/python3`。
