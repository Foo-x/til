# tty1が落ちたときの復帰

tty1が落ちるとキーボード入力画面のような画面に入るが入力を受け付けない状態になる。  
Ctrl + Alt + F3 でtty3などに入って `sudo systemctl restart display-manager` でディスプレイマネージャーを再起動すると復帰できる。
