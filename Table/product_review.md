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
(1, 1, 2, 'Кроссовки супер! Отлично подошли для прогулок и для занятий спортом'),
(2, 2, 4, 'Хорошее качество, но немного дорого'),
(3, 3, 3, 'Нормальный продукт, соответствует описанию. Буду рекомендовать'),
(4, 4, 5, 'Очень доволен покупкой!'),
(5, 5, 2, 'Не оправдал ожидания, есть недостатки.'),
(6, 6, 4, 'В целом неплохо, но есть куда расти'),
(7, 7, 5, 'Не соотвествует заявленному размеру'),
(8, 8, 3, 'Среднее качество, ничего особенного'),
(9, 9, 1, 'Ужасный продукт, не советую покупать.'),
(1, 10, 5, 'Супер! Очень рад приобретению')
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
