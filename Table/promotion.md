# Таблица promotion

### Срипт для создания таблицы

```
CREATE TABLE product_review (
    review_id SERIAL PRIMARY KEY,
    customer_id INTEGER REFERENCES customer (customer_id),
    product_id INTEGER REFERENCES product (product_id),
    rating INTEGER NOT NULL CHECK (rating BETWEEN 1 AND 5),  -- Оценка от 1 до 5
    comment TEXT,
    review_date TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc')
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO product_review (customer_id, product_id, rating, comment) VALUES
(1, 1, 5, 'Отличные кроссовки!')
```

### Назначение таблицы

Хранит информацию о промоакциях и скидках, предлагаемых в магазине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|promotion_id|Уникальный идентификатор промоакции|serial|PRIMARY KEY|
|promotion_name|Название промоакции|varchar(255)|NOT NULL|
|description|Описание|text||
|discount_percentage|Процент скидки (например, 10.00 для 10%)|decimal(10,2)|NOT NULL|
|start_date|Дата начала действия промоакции.|date|NOT NULL|
|end_date|Дата окончания действия промоакции.|date|NOT NULL|
|is_active|Флаг, указывающий, активна ли промоакция|boolean|DEFAULT TRUE|
