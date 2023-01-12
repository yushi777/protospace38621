
# テーブル設計

## users テーブル

| Column             | Type       | Options                                 |
| ------------------ | ---------- | --------------------------------------- |
| email              | string     | null: NOT NULL, foreign_key: ユニーク制約 |
| encrypted_password | string     | null: NOT NULL                          |
| name               | string     | null: NOT NULL                          |
| profile            | text       | null: NOT NULL                          |
| occupation         | text       | null: NOT NULL                          |
| position           | text       | null: NOT NULL                          |

### Association

- has_many :prototypes
- has_many :comments

## prototypes テーブル

| Column     | Type       | Options                              |
| ---------- | ---------- | ------------------------------------ |
| title      | string     | null: NOT NULL                       |
| catch_copy | text       | null: NOT NULL                       |
| concept    | text       | null: NOT NULL                       |
| user       | references | null: NOT NULL, foreign_key: 外部キー |

### Association

- belongs_to :user
- has_many :comments

## comments テーブル

| Column    | Type       | Options                              |
| --------- | ---------- | ------------------------------------ |
| content   | text       | null: NOT NULL                       |
| prototype | references | null: NOT NULL, foreign_key: 外部キー |
| user      | references | null: NOT NULL, foreign_key: 外部キー |

### Association

- belongs_to :user
- belongs_to :prototype