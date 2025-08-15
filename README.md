# Домашнее задание к занятию "Работа с данными (DDL/DML)" - `Хамуро Илья`

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp.

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp.

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос:

ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

### Решение 

<img width="1565" height="767" alt="Снимок экрана 2025-08-15 164342" src="https://github.com/user-attachments/assets/35009f7b-9adf-4f53-935b-cba973713f8d" />

<img width="710" height="368" alt="Снимок экрана 2025-08-15 164356" src="https://github.com/user-attachments/assets/4ecc12ee-3948-412f-80c5-2fb534501c53" />

<img width="570" height="602" alt="Снимок экрана 2025-08-15 173246" src="https://github.com/user-attachments/assets/e6281869-b518-44a1-96c5-4a12d5f6cfea" />

<img width="1306" height="805" alt="Снимок экрана 2025-08-15 174729" src="https://github.com/user-attachments/assets/48bf1f3f-7998-4e8a-9589-3ca09a395d2a" />

### Задание 2

Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)

Название таблицы | Название первичного ключа
customer         | customer_id

### Решение
<img width="766" height="831" alt="Снимок экрана 2025-08-15 175246" src="https://github.com/user-attachments/assets/dd75ef7b-94b6-43ae-8c0e-03a3b421a2c7" />


### Простыня SQL- запросов к первому заданию 

CREATE USER 'sys_temp'@'%' IDENTIFIED BY 'password';n\
SELECT user, host FROM mysql.user;n\
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%';n\
FLUSH PRIVILEGES;n\
SHOW GRANTS FOR 'sys_temp'@'%';n\
ALTER USER 'sys_temp'@'%' IDENTIFIED WITH mysql_native_password BY 'password';n\

USE sakila;n\
SHOW TABLES;n\

### SQL-скрипт по Заданию 2 SELECT 
    TABLE_NAME AS 'Название таблицы',
    COLUMN_NAME AS 'Название первичного ключа'
FROM 
    INFORMATION_SCHEMA.KEY_COLUMN_USAGE
WHERE 
    TABLE_SCHEMA = 'sakila'
    AND CONSTRAINT_NAME = 'PRIMARY'
ORDER BY 
    TABLE_NAME;
