# スクリプトを並列実行してCtrl-Cですべて終了

```bash
(
    trap "exit" INT TERM
    trap "kill 0" EXIT

    (script1) &
    (script2) &

    wait
)
```

1つ目の`trap`はスクリプトがエラーで落ちたときにCtrl-Cが効かなくなるのを防ぐため。  
2つ目の`trap`はCtrl-Cでサブシェルをすべてkillするため。  
上のように`trap`を()に入れてサブシェルにしないと、親シェルごと落ちるので注意。
