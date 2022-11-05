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
` $ chmod +x ****.sh`  

#### 3・・・・実行する
##### 例  
` $ ./****.sh`  

#### 4・・・・ローカルの3306ポートでコネクション待ち状態になるので
##### 例  
` $ ./****.sh`  
 
```
Starting session with SessionId: *********0ff4075884335f2fc  
Port 3306 opened for sessionId *********0ff4075884335f2fc.  
Waiting for connections...  
```

#### 5・・・・mysqlコマンドやベンチマークで接続
  
local  
` $ mysql -uroot -h 127.0.0.1 -P 3306 -p`   
` $ Enter password: (初期パスワード：password)  `


  
remote  
コネクション確立
~~~
Starting session with SessionId: *********0ff4075884335f2fc
Port 3306 opened for sessionId *********0ff4075884335f2fc.
Waiting for connections...

Connection accepted for session [*********0ff4075884335f2fc]  
~~~  

local  
~~~
mysql -uroot -h 127.0.0.1 -P 3306 -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.  
Your MySQL connection id is 18081  
Server version: 8.0.31 MySQL Community Server - GPL  
  
Copyright (c) 2000, 2022, Oracle and/or its affiliates.  
  
Oracle is a registered trademark of Oracle Corporation and/or its  
affiliates. Other names may be trademarks of their respective  
owners.  
  
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.   
mysql> show databases;  
+--------------------+  
| Database           |  
+--------------------+  
| information_schema |  
| laravel_sail_api   |  
| mysql              |  
| performance_schema |  
| sys                |  
| testing            |  
+--------------------+  
6 rows in set (0.02 sec)  
  
mysql>  
~~~  

20221105 update  
