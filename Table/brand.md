# Таблица brand

### Срипт для создания таблицы

```
CREATE TABLE brand (
    brand_id SERIAL PRIMARY KEY,
    brand_name VARCHAR(255) UNIQUE NOT NULL
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO BRAND (brand_name) VALUES
('Nike'),
('Adidas'),
('Puma'),
('Reebok'),
('Demix');
```

### Назначение таблицы

Хранит информацию о брендах спортивных товаров, представленных в магазине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|brand_id|Уникальный идентификатор бренда|serial|PRIMARY KEY|
|brand_name|Имя бренда|varchar(255)|NOT NULL|
