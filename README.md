アプリケーション名
senkyo-app

アプリケーション概要
このアプリケーションでは選挙において立候補者のマニュフェストの確認及び立候補者への投票ができる
URL
https://git.heroku.com/senkyo-app.git

テスト用アカウント
実装していません

利用方法

目指した課題解決	

テーブル設計

洗い出した要件

実装した機能についての画像やGIFおよびその説明

実装予定の機能


#Candidatesテーブル
| Column               | Type    | Options                     |
| -------------------- | ------- | --------------------------- |
| candidate            | string  | null: false                 |
| vote                 | integer |                             |
| pledge               | text    | null: false                 |

has_many :comments

#Usersテーブル
| Column               | Type    | Options                     |
| -------------------- | ------- | --------------------------- |
| email                | string  | null: false                 |
| encrypted_password   | string  | null: false                 |
| my_number            | string  | null: false                 |
| comment_count        | integer |                             |
| vote_count           | integer |                             |

has_one :comment

#Commentsテーブル
| Column               | Type       | Options                        |
| -------------------- | ---------- | ------------------------------ |
| text                 | text       | null: false                    |
| user                 | references | null: false, foreign_key: true |
| candidate            | references | null: false, foreign_key: true |

belongs_to :candidates
belongs_to :user