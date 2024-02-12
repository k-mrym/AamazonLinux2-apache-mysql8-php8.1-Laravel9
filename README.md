# README

```sh
# コンテナを作成する
[mac] $ docker compose up -d

# コンテナを破棄する
[mac] $ docker compose down

# コンテナ、イメージ、ボリュームを破棄する
[mac] $ docker compose down --rmi all --volumes

# コンテナ、ボリュームを破棄する
[mac] $ docker compose down --volumes




### build ###
docker compose up -d --build
docker compose exec web composer create-project --prefer-dist "laravel/laravel" .
docker compose exec web composer require encore/laravel-admin
docker compose exec web php artisan vendor:publish --provider="Encore\Admin\AdminServiceProvider"
docker compose exec web php artisan admin:install

# http://localhost:8080/admin
# 管理画面への初期ID/PASSはadmin/admin


### db ###
docker ps
docker exec -it MySQLのコンテナ名 bash
mysql -u root -p
mysql> show databases;
mysql> use myapp_development;
mysql> show tables;
mysql> select * from テーブル名;

```