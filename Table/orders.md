# Таблица orders

### Срипт для создания таблицы

```
CREATE TABLE orders(
    order_id SERIAL PRIMARY KEY,
    customer_id INTEGER REFERENCES customer (customer_id),
    order_date TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc'),
    total_amount DECIMAL(10, 2) NOT NULL,
    order_status VARCHAR(50) NOT NULL DEFAULT 'Новый',
    shipping_address_id INTEGER REFERENCES shipping_address(address_id),
    payment_method_id INTEGER REFERENCES payment_method(payment_method_id)
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO orders (customer_id, total_amount, order_status, shipping_address_id, payment_method_id) VALUES
(1, 125.50, 'Обработан', 1, 1),
(2, 50.00, 'Отменен', 3, 2),
(3, 75.25, 'В пути', 4, 3),
(4, 200.00, 'Доставлен', 5, 1),
(5, 35.75, 'Новый', 6, 2),
(6, 150.00, 'Обработан', 7, 3),
(7, 90.50, 'В пути', 8, 1),
(8, 60.25, 'Доставлен', 9, 2),
(9, 110.00, 'Новый', 2, 3),
(1, 80.00, 'Обработан', 10, 1),
(2, 25.00, 'Новый', 1, 2),
(3, 68.75, 'В обработке', 4, 3),
(4, 180.00, 'Отправлен', 3, 1),
(4, 42.20, 'Доставлен', 4, 2),
(5, 95.50, 'В пути', 5, 3),
(6, 130.00, 'Доставлен', 6, 1),
(7, 72.80, 'Новый', 7, 2),
(8, 55.00, 'Обработан', 8, 3),
(9, 105.25, 'Отменен', 9, 1),
(8, 30.50, 'Новый', 10, 2);
```

### Назначение таблицы

Хранит информацию о заказах, сделанных покупателями.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|order_id|Уникальный идентификатор заказа|serial|PRIMARY KEY|
|customer_id|Внешний ключ, указывающий на покупателя, которому принадлежит способ оплаты|integer|REFERENCES customer (customer_id)|
|order_date|Дата и время оформления заказа|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|total_amount|Общая сумма заказа|decimal(10,2)|NOT NULL|
|order_status|Статус заказа|varchar(50)|NOT NULL|
|shipping_address_id|Внешний ключ, указывающий на адрес доставки заказа|integer|REFERENCES shipping_address(address_id)|
|payment_method_id|Внешний ключ, указывающий на способ оплаты заказа|integer|REFERENCES payment_method(payment_method_id)|

