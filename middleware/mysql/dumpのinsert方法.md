# dumpのinsert方法

dumpのinsertは特に指定しなければ普通の `INSERT INTO` になる。  
dump時にオプションを付けると変更できる。

- `--insert-ignore`
    - `INSERT IGNORE INTO`
- `--replace`
    - `REPLACE INTO`
