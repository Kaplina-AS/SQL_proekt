# Таблица cart

### Срипт для создания таблицы

```
CREATE TABLE cart (
    cart_id SERIAL PRIMARY KEY,
    customer_id INTEGER REFERENCES customer (customer_id)
)
```
### Скрипт для наполнени таблицы данными

```
INSERT INTO cart (customer_id) VALUES
(1),
(2),
(3),
(4),
(5)
```

### Назначение таблицы

Хранит информацию о корзинах покупателей (товары, которые покупатель добавил в корзину, но еще не оформил заказ).

### Описание полей таблицы

|Название поля|Описание|Тип данных|Ограничение|
|-|-|-|-|
|cart_id|Уникальный идентификатор корзины|serial|PRIMARY KEY|
|customer_id|Внешний ключ, указывающий на покупателя, которому принадлежит корзина|integer|REFERENCES customer (customer_id)|

