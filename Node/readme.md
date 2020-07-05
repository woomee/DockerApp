# Node
- JavaScriptプログラムのビルドや依存するライブラリをダウンロードするビルドツール

## 利用方法
### 方法1 コンテナ内に入って利用する方法
1. コンテナを起動: `docker-compose up -d`
1. コンテナ内に入る: `docker-compose exec node sh`
1. コンテナ内でnodeコマンドを実行
    - コンテナ中の/home/nodeはホストのホームディレクトにマウントされている

### 方法2 コマンドを直接実行する方法
- 実行するコマンドを指定: `docker-compose exec node sh -c "<コマンド>"`
    - 例1: ~/pj1ディレクトリでmy-appというAngularアプリケーションを場合
        - `docker-compose exec node sh -c "cd /home/node/pj1 && ng new my-app"`
    - 例2: ~/pj1ディレクトリのプロジェクトでAngularのサーバを起動する場合
        - `docker-compose exec node sh -c "cd /home/node/pj1 && ng serve -host 0.0.0.0 --port 8080"`

### <注意事項>
1. コンテナによってファイルが生成される場合(`ng new`など)、ファイルの所有者がrootユーザになりホスト側で編集できない場合があります。その場合は`sudo chown`でファイルの所有者を変更してください。
1. docker-compose exec --workdirの指定はバージョンによっては利用できない
    - `docker-compose exec --workdir <実行ディレクトリ> node <コマンド>`
    ```sh
    $ docker-compose exec --workdir /home/node node ng
    ERROR: Setting workdir for exec is not supported in API < 1.35 (1.25)
    ```

## コンテナ中で利用しているソフトウェア
- node:12.18.2-alpine3.12
- bash
- angular/cli
- firebase-tools
- git

## 利用しているポート番号 (ホスト側:コンテナ側)
- "4200:4200"
    - angular cliの開発用サーバのポート
- "9005:9005"
    - firebase loginで利用するポート
- "8080:8080"
    - 一般的なWebサーバで利用するポート
  

# 動作確認環境
- Windows10
- WSL2（Ubuntu 20.04LTS)

## コンテナを作成した方法とメモ
- Dockerfileを作成
    - Angular, Firebaseで利用するソフトウェアを追加
    - Angularでng newするとgitでエラーになるため追加
- docker-compose.ymlを作成

