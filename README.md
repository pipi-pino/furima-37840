# DB設計

## usersテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| nickname           | string             | null: false               |
| encrypted_password | string             | null: false               |
| email              | string             | null: false,unique:true   |
| first_name         | string             | null: false               |
| family_name        | string             | null: false               |
| first_name_kana    | string             | null: false               |
| family_name_kana   | string             | null: false               |
| birth_date         | date               | null: false               |

### Association

* has_many :item
* has_one :credit_card

## itemsテーブル

| Column             | Type               | Options                         |
|--------------------|--------------------|---------------------------------|
| name               | string             | null: false                     |
| description        | text               | null: false                     |
| price              | integer            | null: false                     |
| item_condition     | string             | null: false                     |
| size               | string             | null: false                     |
| shipping_charge    | string             | null: false                     |
| delivery_time      | string             | null: false                     |
| area               | string             | null: false                     |
| category_id        | integer            | null: false                     |
| user_id            | integer            | null: false, foreign_key: true  |

### Association

* belongs_to :user

## credit_cardsテーブル

| Column             | Type               | Options                         |
|--------------------|--------------------|---------------------------------|
| customer_id        | string             | null: false                     |
| card_id            | string             | null: false                     |
| user_id            | integer            | null: false, foreign_key: true  |

### Association

* belongs_to :user

## orderテーブル

| Column             | Type               | Options                         |
|--------------------|--------------------|---------------------------------|
| user_id            | integer            | null: false, foreign_key: true  |
| item_id            | string             | null: false                     |

### Association

* belongs_to :items

## addressテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| phone_number       | string             | null: false               |
| postal_code        | string             | null: false               |
| prefecture         | string             | null: false               |
| city               | string             | null: false               |
| address            | string             | null: false               |
| building_name      | string             | null: false               |

### Association

* belongs_to :order