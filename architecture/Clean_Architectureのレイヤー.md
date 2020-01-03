# Clean Architectureのレイヤー

1. Entities
    - ドメイン固有のルールを扱う
    - 最も抽象的な層
2. Use Cases
    - アプリ固有のルールを扱う
    - Entitiesを組み合わせて問題を解決する層
3. Interface Adapters
    - 外部とのやりとりを扱う
    - 内部のデータを外部用に変換したり、その逆を行う
    - Controller/Presenter/Gateway
4. Frameworks & Drivers
    - 外部での処理を扱う
    - フレームワーク、DBドライバ、外部APIなど
    - 最も具体的な層

大事なのはレイヤーを4つに分けることではなく、内側から外側に依存しないこと
