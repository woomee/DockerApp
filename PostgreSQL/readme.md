# PostgreSQL
- ポートは通常ポートに10000を加えて割り当て
    - PostgreSQL: 15432
    - PgAdmin: 10080
- mount/pginitに*.sqlというファイル名でSQLスクリプトを入れておくと初回起動時に実行する
- データディレクトリはdocker volumeの`pgdata`となっている
    - コンテナを停止させてもデータは消えない
    - データを消すには以下のコマンドを実行する
        ```
        docker volume rm postgresql_pgdata
        ```
    - dockerのbindマウントは以下のようにコメントアウトしているがファイル所有者のエラーになる可能性が高いため。
        - 特にWindows環境
        ```yml:docker-compose.yml
        volumes:
        #- ./mount/data:/var/lib/postgresql/data
        ```
        - エラー: `FATAL:  data directory "/var/lib/postgresql/data" has wrong ownership`
## 起動方法
- `docker-compose.exe up -d`
- PgAdmin4へのアクセス
    - http://(ホスト名):10080
- ログイン/パスワードは全てpostgres/postgres

## インストールしたソフトウェア
- PostgreSQL 11
- PgAdmin4