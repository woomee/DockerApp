# PostgreSQL11
- ポートは通常ポートに20000を加えて割り当て
    - PostgreSQL: 15432
    - PgAdmin: 10080
- データディレクトリはdocker volumeの`pgdata`となっている
    - コンテナを停止させてもデータは消えない
    - データを消すには以下のコマンドを実行する
        ```
        docker volume rm postgresql_pgdata
        ```
## 起動方法
- `docker-compose.exe up -d`
- PgAdmin4へのアクセス
    - http://(ホスト名):10080
- ログイン/パスワードは全てpostgres/postgres

## インストールしたソフトウェア
- PostgreSQL 11
- PgAdmin4