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
| phone_number       | string             | null: false               |
| postal_code        | string             | null: false               |
| prefecture         | string             | null: false               |
| city               | string             | null: false               |
| address            | string             | null: false               |
| building_name      | string             | null: false               |

### Association

* has_many :items, dependent: :destroy
* has_one :credit_card, dependent: :destroy

## itemsテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| name               | string             | null: false               |
| description        | text               | null: false               |
| price              | integer            | null: false               |
| brand              | string             | null: false               |
| item_condition     | string             | null: false               |
| size               | string             | null: false               |
| shipping_charge    | string             | null: false               |
| delivery_time      | string             | null: false               |
| shipping_way       | string             | null: false               |
| category_id        | integer            | null: false               |
| user_id            | integer            | null: false               |

### Association

* has_many :item_images, dependent: :destroy
* belongs_to :category, dependent: :destroy
* belongs_to :brand, dependent: :destroy

## credit_cardsテーブル

| Column             | Type               | Options                         |
|--------------------|--------------------|---------------------------------|
| customer_id        | string             | null: false                     |
| card_id            | string             | null: false                     |
| user_id            | integer            | null: false, foreign_key: true  |

### Association

* belongs_to :user

## item_imagesテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| item_id            | string             | null: false               |
| item_image         | string             | null: false               |

### Association

* belongs_to :item

## categoriesテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| name               | string             | null: false               |

### Association

* has_many :items

## brandsテーブル

| Column             | Type               | Options                   |
|--------------------|--------------------|---------------------------|
| name               | string             | null: false               |

* has_many :items
