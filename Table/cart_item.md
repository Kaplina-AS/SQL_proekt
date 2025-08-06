# Таблица cart_item

### Срипт для создания таблицы

```
CREATE TABLE cart_item (
    cart_item_id SERIAL PRIMARY KEY,
    cart_id INTEGER REFERENCES cart (cart_id),
    product_id INTEGER REFERENCES product (product_id),
    quantity INTEGER NOT NULL
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO cart_item (cart_id, product_id, quantity) VALUES
(1, 3, 2),
(2, 4, 1),
(3, 12, 20),
(4, 9, 3),
(5, 7, 1)
```

### Назначение таблицы

Связывает корзины с конкретными товарами и указывает количество каждого товара в корзине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|cart_item_id|Уникальный идентификатор позиции корзины|serial|PRIMARY KEY|
|cart_id|Внешний ключ, указывающий на корзину, к которой относится позиция|integer|REFERENCES cart (cart_id)|
|product_id|Внешний ключ, указывающий на товар, включенный в корзину|integer|REFERENCES product (product_id)|
|quantity|Количество товара в данной позиции корзины.|integer|NOT NULL|
