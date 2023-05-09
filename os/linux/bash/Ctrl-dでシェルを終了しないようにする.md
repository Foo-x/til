# Ctrl-d でシェルを終了しないようにする

`export IGNOREEOF=2` を実行すると Ctrl-d を連続で3回押さないとシェルが終了しなくなる。  
`set -o ignoreeof` を実行すると `export IGNOREEOF=10` と同等で、Ctrl-d を連続で11回押さないとシェルが終了しなくなる。  
