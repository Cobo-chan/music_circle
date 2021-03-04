# テーブル設計

## usersテーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |

## Association
- has_many :articles
- has_many :comments


## articlesテーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| title      | text       | null: false                    |
| genre_id   | integer    | null: false                    |
| country_id | integer    | null: false                    |
| text       | text       | null: false                    |
| user       | references | null: false, foreign_key: true |

## Association
- has_many :comments
- belongs_to :user

## commentsテーブル

| Column  | Type       | Options     |
| ------- | ---------- | ----------- |
| comment | text       | null: false |
| user    | references | null: false |
| article | references | null: false |

## Association
- belongs_to :user
- belongs_to :article