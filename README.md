## 環境構築
### 必要なもの
- src ディレクトリ配下に .env ファイルを用意してください。

.envファイルを用意した後、以下のコマンドを実行して開発環境の Docker コンテナを作成・起動してください。
```shell
docker-compose up -d --build
```

コンテナの起動が完了したら、php-fpm コンテナで 必要なパッケージをインストールするコマンドを実行します。
```shell
docker exec -it php-fpm bash -c "composer install && npm install && php artisan migrate"
```

### フロントエンドのビルド
フロントエンドのリソースをビルドするために、以下のコマンドを実行します。
```shell
docker exec -it php-fpm bash -c "npm run dev"
```

[http://localhost/](http://localhost/)へアクセスし、レスポンスがあれば環境構築は完了です。


## phpmyadmin
[phpmyadmin](http://localhost:8080)を使用して、アプリケーションのデータベースを GUI で閲覧できます。
