# Gradle
- Javaプログラムのビルドや依存するライブラリをダウンロードするビルドツール

## 利用方法
### 方法1 コンテナ内に入って利用する方法
1. コンテナを起動: `docker-compose up -d`
1. コンテナ内に入る: `docker-compose exec gradle bash`
1. コンテナ内でgradleコマンドを実行
    - コンテナ中の/home/gradleはホストのホームディレクトにマウントされている
### 方法2 gradleコマンドを直接実行する方法
- 実行するコマンドを指定: `docker-compose exec gradle sh -c "<コマンド>"`
    - 例1: ~/pj1ディレクトリでプロジェクト初期化する場合
        - `docker-compose exec gradle sh -c "cd /home/gradle/pj1 && gradle init"`
    - 例2: ~/pj1ディレクトリのプロジェクトをビルドする場合
        - `docker-compose exec gradle sh -c "cd /home/gradle/pj1 && gradle build"`
## <注意事項>
1. コンテナによってファイルが生成される場合(`gradle init`など)、ファイルの所有者がrootユーザになりホスト側で編集できない場合があります。その場合は`sudo chown`でファイルの所有者を変更してください。
1. docker-compose exec --workdirの指定はバージョンによっては利用できない
    - `docker-compose exec --workdir <実行ディレクトリ> gradle <コマンド>`
    ```sh
    $ docker-compose exec -w /home/gradle gradle gradle tasks
    ERROR: Setting workdir for exec is not supported in API < 1.35 (1.25)
    ```

## コンテナ中で利用しているソフトウェア
- gradle:6.5.1-jdk8


# 動作確認環境
- Windows10
- WSL2（Ubuntu 20.04LTS)

## コンテナを作成した方法
- Dockerfileを作成
    - Gradleコンテナを起動したままにできないためbash実行を追加
- docker-compose.ymlを作成

