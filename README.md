## 構築手順

```sh
$ bin/setup
$ docker-compose build
$ docker-compose run --rm backend bin/setup
$ docker-compose up -d
$ open http://localhost:4100
```

## 課題

### 1. Topにお知らせ追加する

- backend
  - `GET /api/notifications` を受け付けるようにする
  - レスポンスのフォーマットは `{"notifications":[{"id":1,"notification":"XXXXX"},{"id":2,"notification":"YYYYY"}]}`
  - ログインしなくてもアクセス可能
- frontend
  - トップページのメインビジュアルっぽい緑の領域の下部(`.banner`の下部)にbackendで追加したAPIのお知らせ情報を表示する

```html
<!-- タグ構造のサンプル -->
<ul>
  <li>お知らせ1</li>
  <li>お知らせ2</li>
</ul>
```

### 2. 関心のあるタグのFeed一覧を追加する

検討中

- ユーザーは関心のあるタグを登録できる
- ヘッダーの`News`メニューをクリックすると関心のあるタグのついているFeedの一覧を作成日の降順で見れる

### 3. RailsでScaffoldするアプリをAPI + SPAで作る

- ログイン機能つきの日記アプリを作る
  - 基本的な機能は日記のCRUD
  - アカウント登録、ログイン、ログアウト機能
  - ユーザーの画像アップロード機能
- APIはRailsの最新版
- SPAは好きなものを使う
