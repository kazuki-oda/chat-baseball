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


アプリ名 野球専用チャットアプリ

このアプリにはグループが元々ありチャットをする事が出来ます。</br>
グループは自由に出入り出来ます

このアプリを作った理由は自分が野球を見る事が好きだからです。</br>
ついでにチャット出来るみたいな物はたまに見ますが専用のチャットアプリを見ないのであったらいいなと思いました。
<h2>グループはこのように最初から作られています。</h2>
https://gyazo.com/bef538edc4383989e38953e117d4afe5
<h2>このようにログインした状態でメッセージを送信する事が出来ます。</h2>
https://gyazo.com/ba42d2edea7a3b815eb27770718844fa

<h2>今後実装予定の内容</h2>
<li>コメントを送信できるようにする</li>
<li>自動更新機能をつける</li>
<li>もう少し使い方が分かりやすいようにする</li>
<li>メッセージが送信された時間を表示させる</li>
