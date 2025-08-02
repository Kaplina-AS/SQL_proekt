# Таблица billing_address

### Срипт для создания таблицы

```
CREATE TABLE billing_address (
    address_id SERIAL PRIMARY KEY,
    address_line_1 VARCHAR(255) NOT NULL,
    address_line_2 VARCHAR(255),
    city VARCHAR(255) NOT NULL,
    state VARCHAR(255),
    zip_code VARCHAR(20) NOT NULL,
    country VARCHAR(255) NOT NULL
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO billing_address (address_line_1, city, zip_code, country) VALUES
('ул. Ленина, 1', 'Москва', '123456', 'Россия')
```

### Назначение таблицы

Хранит адреса, связанные с платежными картами покупателей.  Может отличаться от адреса доставки.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|address_id|Уникальный идентификатор адреса|serial|PRIMARY KEY|
|address_line_1|Адрес 1 строка|varchar(255)|NOT NULL|
|address_line_1|Адрес 2 строка|varchar(255)|NOT NULL|
|city|Город|varchar(255)|NOT NULL|
|state|Область|varchar(255)||
|zip_code|Индекс|varchar(20)|NOT NULL|
|country|Страна|varchar(255)|NOT NULL|

