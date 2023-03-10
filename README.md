## 作業ディレクトリに移動
```
$ cd get_info_by_sql
```

## コンテナイメージのビルド
```
$ docker build . -t get_info_by_sql
```

## コンテナ作成&起動(初回だけ)
ビルドしたコンテナイメージからコンテナを起動
3306ポートを疏通
```
$ docker run -d --name get_info_by_sql -p 3306:3306 get_info_by_sql
```

## コンテナ内に入る
コンテナ内のシェルを起動
```
$ docker exec -it get_info_by_sql bash

```

## コンテナからローカルに戻る
コンテナ内で実行(`control + d`でもOK)
```
# exit
```

## 初期データの作成
コンテナ内で初期データ作成sql実行
```
# mysql -pcollege < employees.sql
```

## データベースへのログイン
```
# mysql -pcollege
```
ログイン後、プロンプトが`mysql> `になる

## データベースの確認と選択
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| employees          |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.01 sec)

mysql> use employees;
```

## データベースからログアウト
```
mysql> exit
```

## コンテナの停止
※ ローカルで実行
```
$ docker stop get_info_by_sql
```

## コンテナの削除
コンテナが停止した状態で
```
$ docker rm get_info_by_sql
```

## コンテナイメージの削除
コンテナが削除された状態で
```
$ docker rmi get_info_by_sql mysql:5.7
```
