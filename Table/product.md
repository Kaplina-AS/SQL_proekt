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
INSERT INTO product (product_name, description, product_price, stock_quantity, category_id, brand_id, image_url) VALUES
('Nike Air Max 270', 'Кроссовки для повседневной носки', 150.00, 50, 1, 1, 'https://example.com/nike_airmax270.jpg'),
('Adidas Tiro 23 Training Pants', 'Тренировочные штаны Adidas', 60.00, 100, 2, 2, 'https://example.com/adidas_tiro.jpg'),
('Puma тренировочный коврик', 'Коврик для йоги и фитнеса', 25.00, 75, 3, 3, 'https://example.com/puma_mat.jpg'),
('Reebok Training Backpack', 'Рюкзак для тренировок', 45.00, 60, 4, 4, 'https://example.com/reebok_backpack.jpg'),
('Demix гантели 2 кг', 'Гантели для фитнеса', 15.00, 120, 3, 5, 'https://example.com/demix_dumbbells.jpg'),
('Nike Pro Combat шорты', 'Компрессионные шорты для тренировок', 40.00, 80, 2, 1, 'https://example.com/nike_pro_shorts.jpg'),
('Adidas Ultraboost 23', 'Беговые кроссовки Adidas', 180.00, 40, 1, 2, 'https://example.com/adidas_ultraboost.jpg'),
('Puma мяч для фитнеса', 'Мяч для пилатеса и фитнеса', 30.00, 90, 3, 3, 'https://example.com/puma_ball.jpg'),
('Reebok шапка для тренировок', 'Шапка для занятий спортом на улице', 20.00, 110, 4, 4, 'https://example.com/reebok_hat.jpg'),
('Demix футболка', 'Футболка для тренировок', 25.00, 150, 2, 5, 'https://example.com/demix_tshirt.jpg'),
('Nike Revolution 6', 'Бюджетные беговые кроссовки Nike', 70.00, 65, 1, 1, 'https://example.com/nike_revolution.jpg'),
('Adidas носки', 'Спортивные носки Adidas', 10.00, 200, 4, 2, 'https://example.com/adidas_socks.jpg');
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
|created_at|Дата и время создания записи о товаре|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|updated_at|Дата и время последнего обновления информации о товаре|timestamp without timezone|DEFAULT (NOW() AT TIME ZONE 'utc')|
|search_vector|Колонка для полнотекстового поиска|TSVECTOR||
