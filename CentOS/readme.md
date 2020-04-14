# CentOS7
- ssh, apacheが動作するコンテナ
- ポートは通常ポートに20000を加えたもので割り当てている
    - http: 20080
    - ssh: 20022
    - 変更する場合はdocker-compose.ymlの`ports`にて
## 起動方法
`docker-compose up -d`
- ログイン/パスワードはroot/password, user/password

## インストールしたソフト
- open-ssh server/client
- apache2.4
- php5.6

