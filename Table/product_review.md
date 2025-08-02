# Таблица product_review

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

Хранит отзывы покупателей о товарах.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|reviiw_id|Уникальный идентификатор отзыва|serial|PRIMARY KEY|
|customer_id|Внешний ключ, указывающий на покупателя, оставившего отзыв|integer|REFERENCES customer (customer_id)|
|product_id|Внешний ключ, указывающий на товар, включенный в корзину|integer|REFERENCES product (product_id)|
|rating|Оценка товара (например, от 1 до 5 звезд)|integer|NOT NULL CHECK (rating BETWEEN 1 AND 5)|
|review_date|Дата и время написания отзыва|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|comment|Текст отзыва|text||
