# docker-laravel-bbs

## 参考

Laravelの環境をDockerで構築するチュートリアル  
https://tech.windii.jp/backend/laravel/laravel-with-docker-compose  

docker-compose.ymlの書き方について解説してみた  
https://qiita.com/yuta-ushijima/items/d3d98177e1b28f736f04

mysqlの永続化とmysql8を使う
https://qiita.com/juhn/items/274e44ee80354a39d872

## docker-compose up -d 後に必要な手順

### .envファイルは.gitignoreに含まれるので設定が必要
DB_CONNECTION=mysql
DB_HOST=mysql-bbs //docker-compose.ymlのサービス名に揃える
DB_PORT=3306
DB_DATABASE=sample
DB_USERNAME=user
DB_PASSWORD=password

### DBへのデータ作成のために下記の実行は必要
$ docker-compose exec app bash //appのサービス内に入る
$ composer dump-autoload
$ php artisan db:seed