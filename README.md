
## users テーブル

| Column   | Type    | Options     |
| -------- | ------- | ----------- |
| name     | string  | null: false |
| email    | string  | null: false |
| password | integer | null: false |

### Association

- has_many :notices
- has_many :medicines

## medicines テーブル

| Column          | Type    | Options                        |
| --------------- | ------- | ------------------------------ |
| medicine_name   | string  | null: false                    |
| all_tablets     | integer | null: false                    |
| 1day_tablet     | integer | null: false                    |
| timezone_id     | integer | null: false                    |
| memo            | text    |                                | 
| user_id         | integer | null: false, foreign_key: true | 

### Association

- belongs_to :user
- has_many :notices

## notices テーブル

| Column      | Type    | Options                        |
| ----------  | ------- | ------------------------------ |
| start_date  | date    | null: false                    |
| end_date    | date    | null: false                    |
| dosing_time | time    | null: false                    |
| user_id     | integer | null: false, foreign_key: true |
| user_id     | integer | null: false, foreign_key: true |

### Association

- belongs_to :medicine
- belongs_to :user
