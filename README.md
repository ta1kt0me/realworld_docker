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

やりたいことは次の２つ

- ユーザーは関心のあるタグを登録/削除できる
- ユーザーは関心のあるタグのArticleの一覧を見れる

[画面イメージ](https://yochiyochirb.slack.com/archives/CM364SBR8/p1567788439016000)
もう少し詳しい仕様や挙動。

- `/@username`のページに`NewsArticles`タブを追加する
- `NewsArticles`タブをクリックすると`/@username/news`を表示する
- `/@username/news`の内容
  - `NewsArticles`タブを選択状態にする
  - 左側にタグの一覧を表示する
  - 右側に選択したタグのArticleの一覧を表示する
- 未選択のタグを選択する
  - user_tagsにレコードを登録するリクエストを発行する
  - タグを選択状態に色を変更する
  - 選択したタグの一覧を含んだArticleの一覧を表示する
- 選択済みのタグを選択する
  - user_tagsにレコードを削除するリクエストを発行する
  - タグを未選択状態に色を変更する
  - 選択したタグの一覧を含んだArticleの一覧を表示する

- backend
  - `POST /api/user_tags`
    - ユーザーの関心のあるタグを追加する
  - `DELETE /api/user_tags/:id`
    - ユーザーの関心のあるタグを削除する
  - `GET /api/articles/feed`
    - 関心のあるタグのニュースの一覧を取得する

### 3. RailsでScaffoldするアプリをAPI + SPAで作る

- ログイン機能つきの日記アプリを作る
  - 基本的な機能は日記のCRUD
  - アカウント登録、ログイン、ログアウト機能
  - ユーザーの画像アップロード機能
- APIはRailsの最新版
- SPAは好きなものを使う
