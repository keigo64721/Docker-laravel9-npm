# Docker-laravel9-npm
## 初期使用方法
### イメージの構築
```
cd docker-laravel9-npm
mkdir src
docker compose build
```
### コンテナ起動
```
docker compose up #Dockerを表で起動する
```
もしくは
```
docker compose up -d #Dockerをバックグラウンドで起動する(デーモンで起動)
```
### 起動しているコンテナの表示
```
docker compose ps
```
app, mysql, nginxの3つのSTATUSがrunnginになっていれば起動できている

### Laravel9のインストール
appコンテナに入る
```
docker compose exec app bash
```
composerがあることを確認
```
composer -V
```
Laravel9プロジェクトを現在のディレクトリで作成
```
composer create-project laravel/laravel --prefer-dist . "9.*"
```
### ブラウザ上でLaravel9にアクセス
ブラウザでURLの欄に``localhost:80``と入力し、Laravel9のWelcome Pageが表示されれば成功

### コンテナを停止
``exit``でコンテナから出てから以下を実行する
```
docker compose down
```

---
## 2回目以降の起動
```
docker compose up -d
```
を行なったのちに``localhost:80``にアクセス

---
## mysqlコンテナにアクセス
```
docker compose exec mysql bash
```
SQlを用いてデータベースやテーブルの管理ができる
