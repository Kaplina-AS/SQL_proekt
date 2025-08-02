# Таблица customer

### Срипт для создания таблицы

```
CREATE TABLE customer (
    customer_id SERIAL PRIMARY KEY,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    phone_number VARCHAR(20),
    address TEXT,
    registration_date TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc'),
    password_hash VARCHAR(255) NOT NULL,
    is_active BOOLEAN DEFAULT TRUE
)
```

### Назначение таблицы

Хранит информацию о зарегистрированных покупателях в интернет-магазине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|customer_id|Уникальный идентификатор покупателя|serial|NOT NULL|
|first_name|Имя покупателя|varchar(255)|NOT NULL|
|last_name|Фамилия покупателя|varchar(255)|NOT NULL|
|email|Адрес электронной почты покупателя|varchar(255)|UNIQUE NOT NULL|
|phone_number|Номер телефона покупателя|varchar(20)||
|address|Адрес покупателя строкой|text||
|registration_date|Дата и время регистрации покупателя. Автоматически устанавливается при создании записи|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|is_active|Флаг, указывающий, активна ли учетная запись покупателя. Позволяет деактивировать учетные записи без удаления данных|boolean|DEFAULT TRUE|

