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
INSERT INTO product (product_name, description, product_price, stock_quantity, category_id, brand_id) VALUES
('Кроссовки Nike Air Max', 'Легкие и удобные кроссовки для бега', 120.00, 50, 1, 1),
('Футболка Adidas Performance', 'Футболка из дышащей ткани для тренировок', 30.00, 100, 2, 2);
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
