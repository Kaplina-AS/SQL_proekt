# Таблица category

### Срипт для создания таблицы

```
CREATE TABLE category (
    category_id SERIAL PRIMARY KEY,
    category_name VARCHAR(255) UNIQUE NOT NULL,
    description TEXT
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO category (category_name) VALUES
('Обувь'),
('Одежда'),
('Инвентарь'),
('Аксессуары'),
('Спортивное питание');
```

### Назначение таблицы

Определяет категории спортивных товаров.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|category_id|Уникальный идентификатор категории|serial|PRIMARY KEY|
|category_name|Название категории|varchar(255)|UNIQUE NOT NULL|
|description|Описани категории|text||
