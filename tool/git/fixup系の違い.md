# fixup系の違い

rebase時にコミットをまとめたりメッセージを変更したりする方法がいくつかある。

- `git commit --fixup <sha>`
    - ステージングしている変更を含むfixupコミットを行う
    - rebase時に `<sha>` のコミットにまとめられる
    - コミットメッセージは `<sha>` のものが使われる
- `git commit --fixup amend:<sha>`
    - ステージングしている変更を含むamendコミットを行う
    - rebase時に `<sha>` のコミットにまとめられる
    - コミットメッセージはamendコミットのものが使われる
- `git commit --fixup reword:<sha>`
    - ステージングしている変更を含まないamendコミットを行う
    - rebase時に `<sha>` のコミットにまとめられる
    - コミットメッセージはamendコミットのものが使われる
- `git commit --squash <sha>`
    - ステージングしている変更を含むsquashコミットを行う
    - rebase時に `<sha>` のコミットにまとめられる
    - rebase時にエディタが開いてコミットメッセージを編集できる
        - その際、初期値としてsquashコミットのものと `<sha>` のものをマージしたものが設定されている
