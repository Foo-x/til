# すべてのブランチをfetch

基本的には `git fetch --all` ですべてのブランチをfetchできる。  
ただ、GitHub CLI のfork元リポジトリなどで特定のブランチしかfetchできないことがある。  
その場合は `.git/config` の `remote.<リモート名>.fetch` に指定されているブランチ名を `*` に変えることで解決できる。

例

```diff
[remote "upstream"]
-  fetch = +refs/heads/main:refs/remotes/upstream/main
+  fetch = +refs/heads/*:refs/remotes/upstream/*
```
