# Laravel Sailで構築したmysql.serverへの接続方法
Localの3306番ポートをリモートの3306へ転送  
mysqlclientのインストール  
(https://qiita.com/fault/items/b854d90ae6eef5aa3417)


#### 1・・・・以下のスクリプトをコピーして任意の名前で保存
##### 例  $ ****.sh

```
#Laravel Sail to mysql PortForward
aws ssm start-session --region "ap-northeast-1"  \
--target i-00a9559e0b777551e  \
--document-name AWS-StartPortForwardingSession  \
--parameters '{"portNumber":["3306"], "localPortNumber":["3306"]}'
```

#### 2・・・・実行権限を付与
##### 例  
$ chmod +x ****.sh

#### 3・・・・実行する
##### 例  $ ./****.sh


