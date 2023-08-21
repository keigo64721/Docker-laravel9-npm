# Docker-laravel9-npm
## 初期使用方法
### ビルド準備
```
cd docker-laravel9-npm
mkdir src
touch .env
```
.envファイルに情報を記載
```
vi .env
```
以下の内容をファイルに記載する(DB系の環境変数は各自で変更する)
```
WEB_PORT=80
DB_PORT=3306
PMA_PORT=8080 

# ここはどんな値でも構わない
DB_NAME=db_name
DB_USER=db_user
DB_PASSWORD=db_password
DB_ROOT_PASSWORD=root
```
### イメージの構築
```
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
