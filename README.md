# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


# trello

バージョン管理
git@github.com:kuimac/trello.git
看板
https://trello.com/b/RtHgBDSL/trello#

##ゴール
trelloのようなカードをD&Dで移動できるwebアプリをつくりherokuで後悔する

##身に付けたい能力
-Drag & Drop APIが面白そうなのでやってみたい
    -testをかけるようになりたい
-weaknessポイントとしてtestをかけないのでテスト駆動開発を取り入れる


##ざっくり開発フロー
1.rails初期設定
1. ログイン機能
1. [ドラッグ＆ドロップで並び替えて順番を保存できるリストを作る](https://qiita.com/at-946/items/28cad21211b9305d6077)
1. カテゴリ機能
1. 画像アップロード機能（ユーザープロフィール・trelloのカード・D&D）


##rails初期設定編

[新規Railsプロジェクトの作成手順まとめ](https://qiita.com/yuitnnn/items/b45bba658d86eabdbb26)
基本的にこちらをなぞりながら進めていく

###1.githubとかGemfileとか
githubでリポジトリ作って
ディレクトリ作って
$ mkdir torrelo
$ cd torrelo

githubのチュートリアル？
initなりmd作るなりやって
first commit

そのあと
$ bundle init

作成されたGemfileの以下のコメントを外した
>gem "rails"


これで準備ができたようなのでRailsをインストールしていく。
$ bundle install --path vendor/bundle

この時に--path vendor/bundleをつけると
プロジェクトのvendor/bundle以下にgemが格納される。
次回以降
 bundle installで自動的にvendor/bundle以下に格納されるので
 --path vendor/bundleは不要

###2. Railsプロジェクトを生成する
$ bundle exec rails new . -B -d mysql --skip-test
>.　現在のディレクトリに作成
>d mysql 　DBをmysqlに指定
>--skip-test　デフォルトのminitestではなくRSpecを使いたいので

redome.mdとGemfileを上書きしていいか聞かれるのでとりあえずy
redomeはそのあと文言復旧


###3. 必要なgemをインストールしてmasterにpush
参考を参考に.gitignoreを編集してgithubにpush!
$ git add .
$ git commit -m"rails初期設定の完了"
$ git push

###最後に
$ bindle install
$rails s
エラー
>Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)
無事起動せず

mysql起動してなかったので再起動(別のターミナル)
$ mysql.server restart
$ mysql -u root
$ rails s

エラー
>Unknown database 'trello_development'
db作ってないやん！

$ rails db:create
$ rails db:migrate
$ rails s

>Yay! You’re on Rails!

無事起動✨

###まとめ
mysqlを起動することやDBを作ることを忘れていたので てへぺろですね。

次は ほぼ静的なページの作成
