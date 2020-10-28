# アプリ名
medicalmanager(メディカルマネージャー)
# 概要
高齢者や物忘れの多い人の為のお薬管理アプリ。カレンダーに一日の服用個数を表記してくれる機能、薬の残数管理機能、服用時間にリマインダーしてくれる機能。（将来的には薬の検索機能を実装予定）
# 制作背景
私の祖母は認知症により薬の管理が難しく、多量に薬をもらってきたり、服用時間を忘れてしまう事が多い為、服用時間を通知でき、残数管理できるアプリがあれば問題の解決に繋がると思い、制作を始めました。また、カレンダーによる残数管理できれば次に病院で処方してもらうタイミングやいつ薬を飲んだのか把握できるのではないかと考えました。
# 実装予定の内容
・残数管理機能
・リマインダー機能
# DB設計
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
