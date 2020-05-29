# README

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|
|id|integer|null: false, unique: true|

<!-- メールアドレス
パスワード　削除 -->

### Association
has_many :messages
has_many :groups, through: :groups_users
has_many :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
belongs_to :group
belongs_to :user



## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|id|integer|null: false, unique: true|
<!-- グループのメンバー　中のメッセージ
グループの名前　削除　 -->
### Association
has_many :messages
has_many :users, through: :groups_users
has_many :groups_users


## メッセージテーブル
|Column|Type|Options|
|------|----|-------|
|image|string||
|content|string||
|user_id|integer|null: false, foreign_key:true|
|group_id|integer|null: false, foreign_key: true|
<!-- user 時間　内容　画像　どのグループのメッセージなのか
削除 -->
### Association
belongs_to :user
belongs_to :group


<!-- ①主要テーブルの洗い出し
②テーブル同士のアソシエーション
    1対多、多対多、なし
    has_many, belongs_toをつける。belongs_toをつけたテーブルに外部キーを追加。
  テーブルに必要なカラムを考える

③中間テーブルの作成
  名前：~s_~sテーブル
  外部キーのカラムを追加
  アソシエーションも組む（belongs_to）
  has_many throughオプションを使う


user_id   group_id
1           2
1           3
1           5
2           3
3           1
3           4

④タイプとオプションの記入
string integer

not null制約
一意性制約
外部キー制約 -->

