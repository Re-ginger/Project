1. Запрос с конструкциями SELECT, JOIN
Вывести все вина (из таблицы wine_production), которые производятся на виноградниках (из таблицы vineyards) с указанием названия виноградника.
```bash
SELECT wp.production_id, v.name AS vineyard_name, wp.wine_type
FROM wine_production wp
JOIN vineyards v ON wp.vineyard_id = v.vineyard_id;
```
 Этот запрос соединяет таблицы wine_production и vineyards по полю vineyard_id. Выводятся идентификатор производства вина, название виноградника и тип вина.
2. Запрос с добавлением данных INSERT INTO
Задача: Добавить новый виноградник в таблицу vineyards и вывести информацию о добавленной строке.

```bash
INSERT INTO vineyards (name, location, area, soil_type, grape_variety, climate, planting_date) VALUES ('Vineyard 2', 'Location 2', 12.5, 'Clay', 'Merlot', 'Continental', '2024-05-01') RETURNING *;
```
Этот запрос добавляет новую запись в таблицу vineyards и возвращает все поля добавленной строки.

3. Запрос с обновлением данных с UPDATE FROM
Обновить тип вина в таблице wine_production на 'Red Wine' для всех записей, где тип вина равен 'White Wine'.
```bash
UPDATE wine_production wp
SET wine_type = 'Red Wine' FROM (SELECT production_id FROM wine_production WHERE wine_type = 'White Wine') AS sub WHERE wp.production_id = sub.production_id;
```
Этот запрос обновляет тип вина на 'Red Wine' для всех записей, где текущий тип вина — 'White Wine'. Вложенный запрос выбирает идентификаторы записей, которые нужно обновить.

4. Запрос на удаление данных с оператором DELETE USING
далить из таблицы bottles все записи, для которых нет соответствующих записей в таблице wine_production.
```bash
DELETE FROM bottles USING wine_production wp WHERE bottles.production_id = wp.production_id AND wp.production_id IS NULL;
```
Этот запрос удаляет из таблицы bottles те записи, которые не имеют соответствующего production_id в таблице wine_production.

5. Запрос с регулярным выражением
Найти все виноградники, названия которых начинаются с буквы 'V'.
```bash
SELECT * FROM vineyards WHERE name ~ '^V';
```
Регулярное выражение ^V означает, что название должно начинаться с буквы 'V'.

6. Запрос с использованием LEFT JOIN и INNER JOIN
Вывести все записи из таблицы wine_production, даже если нет соответствующих записей в таблице batches, и все записи, которые есть в обеих таблицах.
```bash
SELECT wp.production_id, b.batch_id FROM wine_production wp LEFT JOIN batches b ON wp.batch_id = b.batch_id;
SELECT wp.production_id, b.batch_id FROM wine_production wp INNER JOIN batches b ON wp.batch_id = b.batch_id;
```
LEFT JOIN возвращает все записи из wine_production и соответствующие записи из batches. Если нет соответствий, то будут возвращены NULL значения для полей из batches.
INNER JOIN возвращает только те записи, у которых есть соответствие в обеих таблицах.
7. Запрос на добавление данных с выводом информации
Добавить новый сорт вина и вывести информацию о добавленных строках.
```bash
INSERT INTO wine_varieties (production_id, grape_variety_id, wine_type, region, average_price, alcohol_percentage) VALUES (1, 1, 'Rosé', 'Provence', 25.00, 13.5) RETURNING *;
```
Этот запрос добавляет новую запись в таблицу wine_varieties и возвращает все поля добавленной строки.

8. Запрос с обновлением данных с использованием UPDATE FROM
Задача: Обновить продолжительность выдержки в месяцах для всех сортов вина в зависимости от типа вина.
```bash
UPDATE aging a SET duration_months = 12 FROM wine_production wp WHERE a.grape_variety_id = wp.grape_variety_id AND wp.wine_type = 'Red Wine';
```
Этот запрос обновляет продолжительность выдержки в месяцах для всех записей в таблице aging, где тип вина в таблице wine_production равен 'Red Wine'.

9. Пример использования утилиты COPY
Использовать утилиту COPY для импорта данных из CSV файла в таблицу vineyards.
```bash
COPY vineyards (name, location, area, soil_type, grape_variety, climate, planting_date) FROM '/path/to/vineyards.csv' DELIMITER ',' CSV HEADER;
```
Команда COPY импортирует данные из файла vineyards.csv, разделенные запятыми, в таблицу vineyards. Параметр CSV HEADER указывает, что первая строка файла содержит заголовки столбцов.
