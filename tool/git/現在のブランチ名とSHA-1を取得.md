# 現在のブランチ名とSHA-1を取得

- ブランチ名
    - `git rev-parse --abbrev-ref @`
    - 2.22以上であれば `git branch --show-current`
- SHA-1
    - `git rev-parse @`
- SHA-1 (short)
    - `git rev-parse --short @`
