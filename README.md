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

## itemsテーブル

| Column             | Type               | Options                         |
|--------------------|--------------------|---------------------------------|
| name               | string             | null: false                     |
| description        | text               | null: false                     |
| price              | integer            | null: false                     |
| item_condition     | integer            | null: false                     |
| shipping_charge_id | integer            | null: false                     |
| delivery_time_id   | integer            | null: false                     |
| area_id            | integer            | null: false                     |
| category_id        | integer            | null: false                     |
| user               | references         | null: false, foreign_key: true  |

### Association

* belongs_to :user
* has_one :order

## ordersテーブル

| Column             | Type               | Options                         |
|--------------------|--------------------|---------------------------------|
| user               | references         | null: false, foreign_key: true  |
| item               | references         | null: false                     |

### Association

* belongs_to :item
* has_one :address

## addressテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| phone_number       | string             | null: false               |
| postal_code        | string             | null: false               |
| prefecture         | string             | null: false               |
| city               | string             | null: false               |
| address            | string             | null: false               |
| building_name      | string             |                           |
| order_id           | integer            | null: false               |

### Association

* belongs_to :order