## このリポジトリについて
 Dockerで開発環境を共有するためのリポジトリです。
<br />
<br />
## 環境  
データベース：mysql8.0  
言語：ruby2.7  
フレームワーク：Ruby on Rails 6.1
<br />
<br />
## 方法
### Dockerをインストール
[参考](https://qiita.com/ama_keshi/items/b4c47a4aca5d48f2661c)
### 任意のディレクトリにリポジトリをクローン
```
git clone https://github.com/kazuko-1117/rails_docker
```
<br />

### ルートディレクトリに移動
```console
cd rails_docker
```
<br />

### コンテナを作り、Railsの雛形を作成
```console
docker-compose run web rails new . --force --database=mysql
```
<br />

### imageをビルドし直す
```console
docker-compose build
```
<br />

### config/database.ymlをdocker-compose.ymlで設定した値に変更する
```
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: password
  host: db
```
<br />

### コンテナの中にデータベースを作る
```console
docker-compose run web rails db:create
```
<br />

### コンテナをバックグラウンドで起動
```console
docker-compose up -d
```
<br />

### ブラウザでRailsのwelcomeページを確認
`http://localhost:3000`









