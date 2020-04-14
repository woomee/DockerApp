# Guacamole
- リモートデスクトップやsshをWebブラウザから行える
- PostgreSQLも一緒に動作する

## 利用方法
- サーバを起動: `docker-compose up -d`
- Webブラウザでアクセス: `http://(ホスト名):19080/guacamole`
- ログイン/パスワードはguacadmin/guacadmin

## インストールしたソフト
- Guacamole (guacamole, guacd)
- PostgreSQL
- NginX (リバースプロキシが必要な場合に利用。デフォルとではコメントアウト)

## Dockerコンテナについて
参考ページ: https://qiita.com/katuemon/items/97e955f08b7c4b70e827
### 利用した環境やアプリケーション
- Windows10
- GitBash
### 作成方法
- docker-compose.ymlを作成
    - guacamole, guacd, postgresqlを起動
- PostgreSQLの初期化スクリプト作成
    - 以下のコマンドを実行 
        ```
        mkdir -p .\mount\pginit
        docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --postgres > .\mount\pginit\initdb.sql
        ```
        - GitBashで実行するとエラーになるのでコマンドプロンプトで実行する必要あり。
