# Таблица product_promotion

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

Связывает товары с промоакциями, чтобы указать, к каким товарам применяется каждая промоакция.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|promotion_id|Внешний ключ, указывающий на промоакцию|integer|REFERENCES promotion (promotion_id)|
|product_id|Внешний ключ, указывающий на товар|integer|REFERENCES product (product_id)|

PRIMARY KEY (product_id, promotion_id): Составной первичный ключ, гарантирующий, что каждая комбинация товара и промоакции уникальна.