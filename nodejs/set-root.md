# rootからの相対パス指定

以下の構成とする。
```
app
├─aaa
│  └─bbb
└─ccc
```

環境変数のNODE_PATHにrootのパスを与えると、bbbからcccをimportするときに以下のように書ける。
`import ccc from 'ccc'`

package.jsonのscriptsに、`"cmd": "NODE_PATH='.' command"`と登録しておくと便利。
