# Таблица order_item

### Срипт для создания таблицы

```
CREATE TABLE order_item (
    order_item_id SERIAL PRIMARY KEY,
    order_id INTEGER REFERENCES orders (order_id),
    product_id INTEGER REFERENCES product (product_id),
    quantity INTEGER NOT NULL,
    price_per_unit DECIMAL(10, 2) NOT NULL
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO order_item (order_id, product_id, quantity, price_per_unit) VALUES
(101, 1, 2, 25.00),  
(101, 2, 1, 50.50),  
(102, 3, 3, 10.00),  
(103, 4, 1, 75.25),  
(104, 5, 2, 100.00), 
(105, 6, 1, 35.75),  
(106, 7, 2, 75.00),  
(107, 8, 1, 90.50),  
(108, 9, 3, 20.00),  
(109, 10, 1, 110.00); 

```

### Назначение таблицы

Связывает заказы с конкретными товарами и указывает количество каждого товара в заказе.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|order_item_id|Уникальный идентификатор позиции заказа|serial|PRIMARY KEY|
|order_id|Внешний ключ, указывающий на заказ, к которому относится позиция|integer|REFERENCES orders (order_id)|
|product_id|Внешний ключ, указывающий на товар, включенный в заказ|integer|REFERENCES product (product_id)|
|quantity|Количество товара в данной позиции заказа|integer|NOT NULL|
|price_per_unit|Цена за единицу товара в данной позиции заказа (может отличаться от текущей цены товара, если цена товара изменилась после оформления заказа)|decimal(10,2)|NOT NULL|

