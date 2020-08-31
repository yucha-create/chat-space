# DB設計

## usersテーブル 
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many :message
- has_many :users_groups
- has_many  :groups,  through:  :users_groups

## groupsテーブル 
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
### Association
- has_many :message
- has_many :users_groups
- has_many  :users,  through:  :users_groups

## messagesテーブル 
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group


## users_groupsテーブル 
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group