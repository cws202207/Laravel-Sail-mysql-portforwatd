# クライアントからLaravel Sailで構築したmysqlへの接続方法

### 1・・・・以下のスクリプトをコピーして任意の名前で保存
例  $ ****.sh

```
####Laravel Sail to mysql PortForward
aws ssm start-session --region "ap-northeast-1"  \
--target i-00a9559e0b777551e  \
--document-name AWS-StartPortForwardingSession  \
--parameters '{"portNumber":["3306"], "localPortNumber":["3306"]}'
```

### 2・・・・実行権限を付与
例  $ chmod +x ****.sh

### 3・・・・実行する
例  $ ./****.sh


