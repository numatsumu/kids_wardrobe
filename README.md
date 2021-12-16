# テーブル設計

## users テーブル

| Column              | Type   | Options                   |
| ------------------- | ------ | ------------------------- |
| nickname            | string | null: false               |
| email               | string | null: false, unique: true |
| encrypted_password  | string | null: false               |
| birthday            | date   | null: false               |

### Association

- has_many :outers
- has_many :tops
- has_many :bottoms
- has_many :underwears
- has_many :footwears
- has_many :orders

## outers テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| purchase_day    | date       |                                |
| size_id         | integer    | null: false                    |
| color_id        | integer    | null: false                    |
| season_id       | integer    | null: false                    |
| purpose         | string     |                                |
| memo            | text       |                                |
| brand           | string     |                                |
| have_or_not_id  | integer    | null: false                    |
| transferable_id | integer    | null: false                    |
| user            | references | null: false, foreign_key: true |

### Association

- has_many :outer_bottoms
- has_many :bottoms, through: :outer_bottoms

- belongs_to :user

- has_one :order

## tops テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| type_tops_id    | integer    | null: false                    |
| purchase_day    | date       |                                |
| size_id         | integer    | null: false                    |
| color_id        | integer    | null: false                    |
| season_id       | integer    | null: false                    |
| purpose         | string     |                                |
| memo            | text       |                                |
| brand           | string     |                                |
| have_or_not_id  | integer    | null: false                    |
| transferable_id | integer    | null: false                    |
| user            | references | null: false, foreign_key: true |

### Association

- has_many :top_bottoms
- has_many :bottoms, through: :top_bottoms

- belongs_to :user

## bottoms テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| type_bottoms_id | integer    | null: false                    |
| purchase_day    | date       |                                |
| size_id         | integer    | null: false                    |
| color_id        | integer    | null: false                    |
| season_id       | integer    | null: false                    |
| purpose         | string     |                                |
| memo            | text       |                                |
| brand           | string     |                                |
| have_or_not_id  | integer    | null: false                    |
| transferable_id | integer    | null: false                    |
| user            | references | null: false, foreign_key: true |

### Association

- has_many :outer_bottoms
- has_many :outers, through: :outer_bottoms

- has_many :top_bottoms
- has_many :tops, through: :top_bottoms

- belongs_to :user

## underwears テーブル

| Column            | Type       | Options                        |
| ----------------- | ---------- | ------------------------------ |
| type_underwear_id | integer    | null: false                    |
| purchase_day      | date       |                                |
| size_id           | integer    | null: false                    |
| color_id          | integer    | null: false                    |
| season_id         | integer    | null: false                    |
| purpose           | string     |                                |
| memo              | text       |                                |
| brand             | string     |                                |
| have_or_not_id    | integer    | null: false                    |
| transferable_id   | integer    | null: false                    |
| user              | references | null: false, foreign_key: true |

### Association

- belongs_to :user

## footwears テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| type_footwear_id | integer    | null: false                    |
| purchase_day     | date       |                                |
| size_footwear_id | integer    | null: false                    |
| color_id         | integer    | null: false                    |
| season_id        | integer    | null: false                    |
| purpose          | string     |                                |
| memo             | text       |                                |
| brand            | string     |                                |
| have_or_not_id   | integer    | null: false                    |
| transferable_id  | integer    | null: false                    |
| user             | references | null: false, foreign_key: true |

### Association

- belongs_to :user

## outer_bottoms テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| outer  | references | null: false, foreign_key: true |
| bottom | references | null: false, foreign_key: true |

### Association

- belongs_to :outer
- belongs_to :bottom

## top_bottoms テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| top    | references | null: false, foreign_key: true |
| bottom | references | null: false, foreign_key: true |

### Association

- belongs_to :top
- belongs_to :bottom