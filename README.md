# nextjs-tutorial
Next.jsのチュートリアルをやっていくリポジトリ。

並行してDockerの確認も行っていく。

## Setup
予めNext.jsの初期化だけを破棄前提のコンテナで済ませる。

Docker内のワーキングディレクトリ(WORK_DIR)については詰まったところをQiitaで少し覚え書きしている。

https://qiita.com/devtoku/items/b88fc68d874b787a541e

JavaScriptの場合

```

docker-compose run --rm node npx create-next-app {directory name}
```

TypeScriptの場合

```

docker-compose run --rm node npx create-next-app {directory name} --ts
```

注：nodeの部分はdocker-compose.ymlのサービス名に、directory nameは同ymlのcommandで移動するディレクトリにする。


rmオプションをつけると、runされたときのコンテナが自動で破棄される。

こうすることで、次回以降は`npm run dev`（開発時に使用するローカルホストを立ち上げるコマンド）するだけでよくなる。

今回はdocker-compose.yml内でcommandを指定しているので、`docker-compose up` or `docker-compose start`するだけでいい。

快適！

## 実際に開発を行う
前項で述べているように、すでに事前に必要なファイルは`create-next-app`で作成済み。

あとはコンテナを起動すれば、先程作成されたファイル群から自動でページが生成される。

```

#初回立ち上げ時とコンテナ破棄時
docker-compose up # <-> down
#コンテナをいちいち破棄したくない場合
docker-compose start # <->stop
```

このあとローカルホスト3000番にアクセスすれば、無事ウェルカムページが表示されるはず。
