# Clean Architectureのレイヤー

1. Enterprise Business Rules
    - ドメイン固有のルールを扱う
    - 最も抽象的な層
2. Application Business Rules
    - アプリ固有のルールを扱う
    - Entitiesを組み合わせて問題を解決する層
    - 以下のインタフェースを持つ
        - ゲートウェイ
            - Web API との入出力を扱う
        - リポジトリ
            - DBとの入出力を扱う
3. Interface Adapters
    - 外部とのやりとりを扱う
    - 内部のデータを外部用に変換したり、その逆を行う層
    - 要素の例
        - コントローラ
            - 外部からの入力をハンドリングする
        - プレゼンター
            - 外部への出力を整形する
        - ゲートウェイ、リポジトリの実装クラス
4. Frameworks & Drivers
    - 外部での処理を扱う
    - 最も具体的な層
    - 外部の例
        - フレームワーク
        - DBドライバ
        - Web API
        - ファイルシステム
        - UI

大事なのはレイヤーを4つに分けることではなく、内側から外側に依存しないこと

最も細かく分けた場合のディレクトリ構造の例

```
.
└── src
    ├── adapters            // Interface Adapters 層
    │   ├── controllers     // 入力に関するコード
    │   ├── gateways        // Webとのやり取りに関するコードの実装
    │   ├── presenters      // 出力に関するコード
    │   └── repositories    // DBとのやり取りに関するコードの実装
    ├── entities            // Enterprise Business Rules 層
    ├── infra               // Frameworks & Drivers 層
    │   ├── apis            // Web API に関するコード
    │   ├── db              // DBに関するコード
    │   ├── frameworks      // フレームワークに関するコード
    │   ├── fs              // ファイルシステムに関するコード
    │   └── views           // UIに関するコード
    └── application         // Application Business Rules 層
        ├── gateways        // Webとのやり取りに関するコードのインタフェース
        ├── repositories    // DBとのやり取りに関するコードのインタフェース
        └── usecases        // ユースケースに関するコードのインタフェース
            └── interactors // ユースケースに関するコードの実装
```
