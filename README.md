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

# usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false| 
|password|string|null: false| 
|name|string|null: false,unique: true,index: true| 

### Association
- has_many :messages
- has_many :groups,through: :groups_users
- has_many :groups_users

## groups＿usersテーブル
|Column|Type|Options|
|------|----|-------|
|groups_id|integer|null: false, foreign_key: true, index|
|user_id|integer|null: false, foreign_key: true, index|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, index|
|name|string|null: false|

### Association
- has_many :groups_users
- has_many :groups, through: :groups_users
- has_many :messages
- has_many :comment

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
- has_many :comment

## commentsテーブル

|Column|Type|Options|
|------|----|-------|
|message_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, doreign_key:true
|body|text

### Association
- belongs_to :message


<h2>アプリ名</h2> 
  野球専用チャットアプリ

<h2>本番環境</h2>

<h2>概要</h2>
このアプリにはグループが元々ありチャットをする事が出来ます。</br>
グループは自由に出入り出来ます。
<h2>制作背景</h2>
このアプリを作った理由は自分が野球を見る事が好きだからです。</br>
ついでにチャット出来るみたいな物はたまに見ますが専用のチャットアプリを見ないのであったらいいなと思いました。
そしてこのアプリを作りながらスキルアップを目指す。
<h2>グループはこのように最初から作られています。</h2>
https://gyazo.com/1108e5901463a5328ed979bf30ae7d0f
<h2>このようにログインした状態でメッセージを送信する事が出来ます。</h2>
"https://gyazo.com/ba42d2edea7a3b815eb27770718844fa"
<h2>ユーザー情報編集が出来ます。メッセージ送信者の名前も変わっています</h2>
  https://gyazo.com/383f4bb02840761acc3c93c491a2244c
  
<h2>今後実装予定の内容</h2>
<li>コメントを送信できるようにする</li>
  個人宛にコメントする機能もあることでじっくり会話できるようになると思った為実装したい
<li>自動更新機能をつける</li>
  チャット機能に自動更新機能は必須だから。無かったら会話がリロードされないと更新されない為ものすごく不便
<li>もう少し使い方が分かりやすいようにする</li>
  ビューでボタン等の項目をわかりやすくして利用者がわかりやすくする為
<li>メッセージが送信された時間を表示させる</li>
  いつ送信されたメッセージがわからないとコメントをするときに不便だと思うので実装したい
  
  <h2>課題</h2>
  今後実装予定の機能を全て完璧に実装する為にたくさん勉強しコードをたくさん書いていく</br>
  サーバーサイドとJavaScriptの理解が浅い
  
 <h2>工夫したポイント</h2>
  とにかく野球好きな人が使いやすいようにグループを作った。</br>
  特定の球団が好きな人はその球団のグループでチャットできる。</br>
  何となくこっちのリーグの方が好きな人や、球団より野球自体が好きな人でも入りやすいように工夫した。</br>
  ビューはまだ未完成だがユーザーのことを考えると派手すぎると見えづらいのでそこを気をつける。

<h2>使用技術</h2>
<li>HTML/CSS</li>
<li>Ruby on Rails</li>
<li>JavaScript(今後使用予定)</li>
<li>AWS</li>
<li>MySQL</li>