テーブル設計

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