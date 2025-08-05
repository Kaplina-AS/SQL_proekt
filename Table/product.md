# Таблица product

### Срипт для создания таблицы

```
CREATE TABLE product (
    product_id SERIAL PRIMARY KEY,
    product_name VARCHAR(255) NOT NULL,
    description TEXT,
    product_price DECIMAL(10, 2) NOT NULL,
    stock_quantity INTEGER NOT NULL DEFAULT 0,
    category_id INTEGER REFERENCES category (category_id),
    brand_id INTEGER REFERENCES brand (brand_id),
    image_url VARCHAR(255),
    created_at TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc'),
    updated_at TIMESTAMP WITHOUT TIME ZONE DEFAULT (NOW() AT TIME ZONE 'utc')
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO product (product_name, category_id, product_price) VALUES
('Кроссовки беговые', 1, 120.00),
('Футболка спортивная', 2, 30.00),
('Шорты спортивные', 2, 40.00),
('Рюкзак спортивный', 7, 60.00),
('Протеин сывороточный', 8, 50.00),
('Шейкер спортивный', 8, 15.00),
('Кеды повседневные', 1, 80.00),
('Толстовка спортивная', 2, 70.00),
('Беговая дорожка', NULL, 1000.00),
('Гантели 5 кг', 6, 25.00); 
```

### Назначение таблицы

Хранит основную информацию о каждом товаре в магазине.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|product_id|Уникальный идентификатор товара|serial|PRIMARY KEY|
|product_name|Название товара|varchar(255)|NOT NULL|
|description|Описани товара|text||
|product_price|Цена товара|decimal(10,2)|NOT NULL|
|stock_quantity|Количество товара в наличии на складе|integer|NOT NULL DEFAULT 0|
|category_id|Внешний ключ, указывающий на категорию, к которой принадлежит товар|integer|REFERENCES category (category_id)|
|brand_id|Внешний ключ, указывающий на бренд товара|integer|REFERENCES brand (brand_id)|
|image_url|URL-адрес изображения товара|varchar(255)||
|created_at|Описани товара|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|updated_at|Описани товара|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|search_vector|Описани товара|TSVECTOR||
