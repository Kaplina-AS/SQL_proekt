# Таблица product_promotion

### Срипт для создания таблицы

```
CREATE TABLE product_promotion (
    product_id INTEGER REFERENCES product (product_id),
    promotion_id INTEGER REFERENCES promotion (promotion_id),
    PRIMARY KEY (product_id, promotion_id)  -- Составной первичный ключ
);
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO product_promotion (product_id, promotion_id) VALUES
(1, 1),   
(2, 1),  
(3, 2),   
(4, 2),  
(5, 3),   
(6, 4),   
(7, 4),   
(8, 5),   
(9, 5),   
(10, 1);  
```

### Назначение таблицы

Связывает товары с промоакциями, чтобы указать, к каким товарам применяется каждая промоакция.

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|promotion_id|Внешний ключ, указывающий на промоакцию|integer|REFERENCES promotion (promotion_id)|
|product_id|Внешний ключ, указывающий на товар|integer|REFERENCES product (product_id)|

PRIMARY KEY (product_id, promotion_id): Составной первичный ключ, гарантирующий, что каждая комбинация товара и промоакции уникальна.