FROM node:12.18.2-alpine3.12

# Angularとfirebaseのcliをインストール
RUN npm install -g @angular/cli
RUN npm install -g firebase-tools

# ng newするとgitでエラーになるため追加
RUN apk add git

# pushd/popdなどが使えない
RUN apk add bash