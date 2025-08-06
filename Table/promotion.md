# Таблица promotion

### Срипт для создания таблицы

```
CREATE TABLE promotion (
    promotion_id SERIAL PRIMARY KEY,
    promotion_name VARCHAR(255) NOT NULL,
    description TEXT,
    discount_percentage DECIMAL(5,2) NOT NULL,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    is_active BOOLEAN DEFAULT TRUE
);
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO promotion (promotion_name, description, discount_percentage, start_date, end_date) VALUES
('Летняя распродажа', 'Скидки на все летние товары', 10.00, '2023-06-01', '2023-08-31'),
('Чёрная пятница', 'Грандиозные скидки на все категории товаров', 25.00, '2023-11-24', '2023-11-24'),
('Киберпонедельник', 'Скидки на электронику и гаджеты', 15.00, '2023-11-27', '2023-11-27'),
('Новогодняя акция', 'Скидки на подарки к новому году', 20.00, '2023-12-15', '2024-01-07'),
('Весенние скидки', 'Скидки на весеннюю коллекцию', 30.0, '2024-03-01', '2024-05-31');
```

### Назначение таблицы

Хранит информацию о промоакциях и скидках, предлагаемых в магазине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|promotion_id|Уникальный идентификатор промоакции|serial|PRIMARY KEY|
|promotion_name|Название промоакции|varchar(255)|NOT NULL|
|description|Описание|text||
|discount_percentage|Процент скидки (например, 10.00 для 10%)|decimal(10,2)|NOT NULL|
|start_date|Дата начала действия промоакции.|date|NOT NULL|
|end_date|Дата окончания действия промоакции.|date|NOT NULL|
|is_active|Флаг, указывающий, активна ли промоакция|boolean|DEFAULT TRUE|
