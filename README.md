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

# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|usersname|string|null: false|
### Association
- has_many :groups
- has_many :message
_ has_many :groups_users
_ has_many :groups,  through:  :groups_users


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|image|strings||
|text|text||
|user_id|integer|null: false, foreign_key: true|
### Association
- has_many :user
- has_many :message
_ has_many :users,  through:  :groups_users

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :groups

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
