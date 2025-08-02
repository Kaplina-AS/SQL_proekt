# Таблица order_item

### Срипт для создания таблицы

```
CREATE TABLE order_item (
    order_item_id SERIAL PRIMARY KEY,
    order_id INTEGER REFERENCES "order" (order_id),
    product_id INTEGER REFERENCES product (product_id),
    quantity INTEGER NOT NULL,
    price_per_unit DECIMAL(10, 2) NOT NULL
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO order_item (order_id, product_id, quantity, price_per_unit) VALUES
(1, 1, 1, 120.00),
(1, 2, 1, 30.00)
```

### Назначение таблицы

Связывает заказы с конкретными товарами и указывает количество каждого товара в заказе.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|order_item_id|Уникальный идентификатор позиции заказа|serial|PRIMARY KEY|
|order_id|Внешний ключ, указывающий на заказ, к которому относится позиция|integer|REFERENCES orders (order_id)|
|product_id|Внешний ключ, указывающий на товар, включенный в заказ|integer|REFERENCES product (product_id)|
|quantity|оличество товара в данной позиции заказа|integer|NOT NULL|
|price_per_unit|Цена за единицу товара в данной позиции заказа (может отличаться от текущей цены товара, если цена товара изменилась после оформления заказа)|decimal(10,2)|NOT NULL|

