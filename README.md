# テーブルの設計

## users テーブル

| Column     | Type        | Option       |
| -----------|------------ | ------------ |
| email      | string      | null: false  |
| password   | string      | null: false  |
| name       | string      | null: false  |
| profile    | text        | null: false  |
| occupation | text        | null: false  |
| position   | text        | null: false  |

### Association
- has_many :prototypes
- has_many :comments

## prototypes テーブル

| Column     | Type        | Option           |
| -----------|------------ | ---------------- |
| title      | string      | null: false      |
| catch_copy | text        | null: false      |
| concept    | text        | null: false      |
| user       | references  | foreign_key: true|

### Association
- belongs_to :user
- has_many :comments
- has_one_attached :image

## comments テーブル

| Column     | Type        | Option            |
| -----------|------------ | ----------------- |
| text       | text        | null: false       |
| user       | references  | foreign_key :true |
| prototype  | references  | foreign_key :true |

### Association
- has_many :users
- has_many :prototypes