# Таблица shipping_address

### Срипт для создания таблицы

```
CREATE TABLE shipping_address (
    address_id SERIAL PRIMARY KEY,
    customer_id INTEGER NOT NULL REFERENCES customer (customer_id),
    house VARCHAR(20) NOT NULL,    
    street VARCHAR(255) NOT NULL,      
    apartment VARCHAR(20),           
    building VARCHAR(255),                  
    city VARCHAR(255) NOT NULL,
    postal_code VARCHAR(20) NOT NULL,
    country VARCHAR(255) NOT NULL,
    created_at TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc'),
    updated_at TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc')
);
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO shipping_address (customer_id, house, street, apartment, building, city, postal_code, country) VALUES
(1, '10', 'Тверская', '5', NULL, 'Москва', '123456', 'Россия'),
(1, '22', 'Арбат', NULL, NULL, 'Москва', '123001', 'Россия'),
(2, '28', 'Невский проспект', '12', NULL, 'Санкт-Петербург', '190000', 'Россия'),
(3, '15', 'Пушкина', '3', 'А', 'Екатеринбург', '620000', 'Россия'),
(4, '7', 'Ленина', NULL, NULL, 'Казань', '420000', 'Россия'),
(5, '33', 'Гагарина', '10', NULL, 'Новосибирск', '630000', 'Россия'),
(6, '1', 'Центральная', NULL, '1', 'Сочи', '354000', 'Россия'),
(7, '9', 'Морская', '7', NULL, 'Владивосток', '690000', 'Россия'),
(8, '4', 'Солнечная', NULL, NULL, 'Краснодар', '350000', 'Россия'),
(9, '18', 'Зеленая', '2', NULL, 'Ростов-на-Дону', '344000', 'Россия');
```

### Назначение таблицы

Хранит адреса доставки покупателей.  Позволяет покупателю иметь несколько адресов доставки

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|address_id|Уникальный идентификатор адреса|serial|PRIMARY KEY|
|customer_id|Внешний ключ, указывающий на покупателя, которому принадлежит адрес.|integer|REFERENCES customer (customer_id)|
|house|Номер дома|varchar(255)|NOT NULL|
|street|Улица|varchar(255)|NOT NULL|
|apartment|Квартира|varchar(255)|NOT NULL|
|building|Строение/корпус|varchar(255)|NOT NULL|
|city|Город|varchar(255)|NOT NULL|
|country|Страна|varchar(255)||
|postal_code|Индекс|varchar(20)|NOT NULL|
|created_at|Временная метка создания записи. Автоматически заполняется текущим временем в UTC.|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|updated_at|ДВременная метка последнего обновления записи. Автоматически заполняется текущим временем в UTC.|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|

