# composeとswarmとkubernetes

複数のコンテナを扱う有名なツールとして、Docker Compose、Docker Swarm、Kubernetesがある。

- Docker Compose
    - 1台のマシンで複数コンテナからなるサービスを扱う
- Docker Swarm
    - 複数マシンからなるクラスタを扱う
- Kubernetes
    - Docker Swarm と同じ立ち位置だが、より高機能で複雑
    - Docker Swarm にない機能の例として、オートスケールやロールベースのアクセス制御などがある
    - サービスメッシュを導入できる有名なツールにIstioがある
