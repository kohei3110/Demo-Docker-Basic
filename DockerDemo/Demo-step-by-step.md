## デモ前

```
# VS Code Remote Container 起動

# コンテナ削除
docker rm <container id>

# イメージ削除
docker rmi <image id>

# キャッシュクリア
docker system prune -a
```

## nginx

```
# nginx イメージを pull（コンテナ作成）
docker pull nginx:latest

# イメージ確認
docker images

# nginx コンテナ起動
docker run --name sample-nginx -d -p 8000:80 nginx:latest

# 起動中のコンテナ確認
docker ps

# nginx へリクエスト
curl http://localhost:8000

# nginx のトップページをカスタマイズ（ index.html を /usr/share/nginx/html/index.html にコピー）
docker cp ./index.html sample-nginx:/usr/share/nginx/html/index.html

# 再度 nginx へリクエスト（出力が Welcome to Microsoft! に変わっていることを確認する）
curl http://localhost:8000

# コンテナの中に入る
docker exec -it sample-nginx bash

# PID 1 を確認（PID 1 の配下にコンテナプロセスがホストと隔離された空間で実行されていることを確認する）
apt update
apt install -y procps
ps -ef   # PID 1 で nginx が稼働していることがわかる
exit

# ホストOSからみた Docker の PID を確認
docker inspect <コンテナID> | grep Pid
```

## サンプルアプリ

```
# コンテナ作成(初回 110 秒ほど)
docker build -t sample:1.0.0 . 

# イメージ確認
docker images

# コンテナ起動
docker run -d -p 8080:8080 --name sample1 sample:1.0.0

# 起動中のコンテナ確認
docker ps

# リクエスト（Hello World が出力される）
curl http://localhost:8080

# index.js の出力を変更
hello world => hello microsoft

# コンテナ再作成（タグを変更することを忘れない）
docker build -t sample:1.0.1 .

# イメージ確認
docker images

# コンテナ起動
docker run -d -p 8081:8080 --name sample2 sample:1.0.1

# リクエスト（Hello Microsoft が出力される）
curl http://localhost:8081
```

## ご紹介サイト

- [Docker Hub: nginx](https://hub.docker.com/_/nginx)