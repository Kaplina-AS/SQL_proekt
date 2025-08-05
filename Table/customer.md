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
    is_active BOOLEAN DEFAULT TRUE
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO customer (first_name, last_name, email, phone_number, address, registration_date) VALUES
('Иван', 'Иванов', 'ivan@example.com', 'Москва, ул. Тверская, д. 10', 'Москва, ул. Тверская, д. 10', '+79031234567',',  '2022-08-02'),
('Александр', 'Иванов', 'ivanov@example.com', 'Санкт-Петербург, Невский пр., д. 25', '+79169876543',  '2022-12-01'),
('Елена', 'Петрова', 'petrova@example.com', 'Екатеринбург, ул. Ленина, д. 30', '+79265551234', '2023-01-15'),
('Сергей', 'Сидоров', 'sidorov@example.com', 'Казань, ул. Баумана, д. 5', '+79651112233', '2023-02-20'),
('Ольга', 'Смирнова', 'smirnova@example.com', 'Новосибирск, Красный пр., д. 15', '+79852223344', '2023-03-10'),
('Дмитрий', 'Кузнецов', 'kuznetsov@example.com', 'Ростов-на-Дону, ул. Большая Садовая, д. 20', '+79057778899', '2023-04-05'),
('Анна', 'Васильева', 'vasilieva@example.com', 'Самара, ул. Ленинградская, д. 12', '+79153334455', '2023-05-12'),
('Игорь', 'Морозов', 'morozov@example.com', 'Омск, ул. Ленина, д. 8', '+79258889900', '2023-06-25'),
('Наталья', 'Волкова', 'volkova@example.com', 'Челябинск, пр. Ленина, д. 22', '+79634445566','2023-07-08'),
('Андрей', 'Павлов', 'pavlov@example.com', 'Уфа, пр. Октября, д. 35', '+79839990011','2023-08-15'),
('Светлана', 'Лебедева', 'lebedeva@example.com', '2023-09-01')
```

### Назначение таблицы

Хранит информацию о зарегистрированных покупателях в интернет-магазине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|customer_id|Уникальный идентификатор покупателя|serial|PRIMARY KEY|
|first_name|Имя покупателя|varchar(255)|NOT NULL|
|last_name|Фамилия покупателя|varchar(255)|NOT NULL|
|email|Адрес электронной почты покупателя|varchar(255)|UNIQUE NOT NULL|
|phone_number|Номер телефона покупателя|varchar(20)||
|address|Адрес покупателя строкой|text||
|registration_date|Дата и время регистрации покупателя. Автоматически устанавливается при создании записи|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|is_active|Флаг, указывающий, активна ли учетная запись покупателя. Позволяет деактивировать учетные записи без удаления данных|boolean|DEFAULT TRUE|

