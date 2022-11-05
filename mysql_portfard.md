# Laravel Sail mysql.serverへの接続方法
Localの3306番ポートをリモートの3306へ転送  

mysqlclientのインストール  
(https://qiita.com/fault/items/b854d90ae6eef5aa3417)


#### 1・・・・以下のスクリプトをコピーして任意の名前で保存
##### 例  $ ****.sh

localでmysql.serverを実行しているとポートが被るので、3307などにlocalPortNumberを変更して下さい。  

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

#### 4・・・・ローカルの3306ポートでコネクション待ち状態になるので

$ ./****.sh 
 
```
Starting session with SessionId: t-saito-0ff4075884335f2fc  
Port 3306 opened for sessionId t-saito-0ff4075884335f2fc.  
Waiting for connections...  
```

#### 5・・・・mysqlコマンドやベンチマークで接続

例  local  
$ mysql -uroot -h 127.0.0.1 -P 3306 -p  
$ password (初期パスワード：password)  


例  remote  
コネクション確立
Connection accepted for session [t-saito-0ff4075884335f2fc]

