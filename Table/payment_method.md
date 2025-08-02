# Таблица payment_method

### Срипт для создания таблицы

```
CREATE TABLE payment_method (
    payment_method_id SERIAL PRIMARY KEY,
    customer_id INTEGER REFERENCES customer (customer_id),
    card_number VARCHAR(20) NOT NULL,  -- Хранить зашифрованным в реальной системе!
    expiry_date DATE NOT NULL,
    cvv VARCHAR(4) NOT NULL,  -- Хранить зашифрованным!
    billing_address_id INTEGER REFERENCES billing_address(address_id)
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO payment_method (customer_id, card_number, expiry_date, cvv, billing_address_id) VALUES
(1, '1234567890123456', '2025-12-31', '123', 1)
```

### Назначение таблицы

Хранит информацию о способах оплаты, которые покупатели используют для совершения покупок (например, кредитные карты).

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|payment_method_id|Уникальный идентификатор способа оплаты|serial|PRIMARY KEY|
|customer_id|Внешний ключ, указывающий на покупателя, которому принадлежит способ оплаты|integer|REFERENCES customer (customer_id)|
|card_number|Номер карты|varchar(20)|NOT NULL|
|expiry_date|Дата окончания срока действия кредитной карты|date|NOT NULL|
|cvv|CVV-код|varchar(4)|NOT NULL|
|billing_address_id|Внешний ключ, указывающий на адрес выставления счетов, связанный с этой платежной картой|integer|REFERENCES billing_address(address_id)|

