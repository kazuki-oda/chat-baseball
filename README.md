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


<h2>アプリ名</h2> 
  野球専用チャットアプリ

<h2>本番環境</h2>
https://chat-baseball.herokuapp.com/</br>
メールアドレス ooo@ooo</br>
パスワード aaaaaa

<h2>概要</h2>
野球に特化したチャットアプリです。</br>
「特定の好きな球団について語りたい」「リーグについて語りたい」「野球自体について語りたい」</br>
といった、野球好きといってもいろんなタイプがあるのでそれぞれのニーズに合うように意識して設計しました。

<h2>制作背景</h2>
<h3>制作理由</h3>
このアプリを作った理由は自分が野球を見る事が好きだからです。</br>
野球速報に対してコメントができるようなアプリはよくみますが</br>
チャット専用のアプリを見ないのであったらいいなと思い作成しました。</br>
試合がない時間帯や、オフシーズンでも野球の話で語り合える場を作れると考えたこと理由の一つです。

<h3>グループはこのように最初から作られています。</h3>
<img src="https://user-images.githubusercontent.com/61171618/79305808-073f4980-7f2f-11ea-90b4-fba4c6ba25af.png">


<h3>このようにログインした状態で送信ボタンを押すとメッセージを送信する事が出来ます。</h3>
<img src="https://user-images.githubusercontent.com/61171618/79316947-07941080-7f40-11ea-8de5-20401466bc5e.png">

<h3>送信できました</h3>
<img src="https://user-images.githubusercontent.com/61171618/79317197-6063a900-7f40-11ea-912e-88cb43396ea0.png">

<h3>1枚目の画像の編集ボタンをクリックするとユーザー情報編集画面に遷移しupdateボタンをクリックすると情報編集が出来ます</h3>
<img src="https://user-images.githubusercontent.com/61171618/79317791-16c78e00-7f41-11ea-874e-be0d1d816de1.png">

<h3>ユーザー情報を編集すると、過去に投稿したメッセージのユーザー名も変わります</h3>
 <img src="https://user-images.githubusercontent.com/61171618/79318299-c00e8400-7f41-11ea-94e1-23b1d5c41dce.png">

<h2>今後実装予定の内容</h2>
<li>投稿へのコメント機能追加</li>
<li>自動更新機能追加</li>
<li>ひと目見て何をするボタンかわかるデザインにする</li>
<li>投稿、コメント時間の表示機能</li>
  
<h2>課題</h2>
今後実装予定の機能を全て完璧に実装する為にたくさん勉強しコードをたくさん書いていく</br>
サーバーサイドとJavaScriptの理解が浅い

<h2>工夫したポイント</h2>
チャット画面は文字が見やすい背景にした。</br>
チャットアプリのコンセプトが直感的にわかるようなTOPページのデザインにした。

<h2>使用技術</h2>
<li>HTML/CSS</li>
<li>Ruby on Rails</li>
<li>JavaScript(今後使用予定)</li>
<li>AWS</li>
<li>MySQL</li>

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
