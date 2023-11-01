# mergetoolをキャンセル

`git mergetool` でvimdiffを使う場合、`:q[uit]` で閉じると何も変更しなくてもステージされてしまう。  
`:cq[uit]` でエラー扱いにして閉じることで、`git mergetool` をキャンセルできる。
