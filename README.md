## 構築手順

```sh
$ bin/setup
# 必要な変更を行う
# https://scrapbox.io/jambo/Rails_+_Reactで_realworld_example_appsを動かす
#   以下の項目の diff を取り込む
#   - APIサーバ
#   - SPA
$ docker-compose build
$ docker-compose up -d
$ open http://localhost:4100
```
