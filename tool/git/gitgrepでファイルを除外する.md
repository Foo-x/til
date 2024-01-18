# gitgrepでファイルを除外する

`git grep 'foo' -- ':!*.java' ':!*/tests/*` のように `-- ':!foo'` で検索対象からファイルを除外できる。
