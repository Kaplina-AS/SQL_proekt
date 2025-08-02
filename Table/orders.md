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
INSERT INTO orders (customer_id, total_amount, shipping_address_id, payment_method_id) VALUES
(1, 150.00, 1, 1)
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

