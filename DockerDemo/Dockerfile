FROM node:12

# 以下のようにも書けるが、ビルドに時間がかかるため、簡略化
# FROM ubuntu:18.04
# RUN apt-get update && apt-get install nodejs npm -y

# アプリケーションディレクトリを作成する
WORKDIR /usr/src/app

# アプリケーションの依存関係をインストール
COPY package*.json ./
RUN npm install

# アプリケーションのソースをバンドル
COPY . .

EXPOSE 8080
CMD [ "node", "index.js" ]