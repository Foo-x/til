# リポジトリの改行コードをLFに統一する

```
* text=auto eol=lf
```

と記載した`.gitattributes`をリポジトリのルートに配置すると、gitがテキストファイルと判断したものをコミットする際に改行コードがLFになる。  
コミット済みのものを一括で変換したいときは、`git add --renormalize .`でOK。
