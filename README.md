#chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, index: true|
### Association
- has_many :posts
- has_many :groups,  through:  :users_groups
- has_many :users_groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users,  through:  :users_groups
- has_many :posts
- has_many :users_groups

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|string||
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
