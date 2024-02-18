# [Основные операторы PostgreSQL](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D0%BE%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5-%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%82%D0%BE%D1%80%D1%8B-postgresql)

## Оглавление  
[1. Описание проекта](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%B0)  
[2. Краткая информация о данных](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D0%BA%D1%80%D0%B0%D1%82%D0%BA%D0%B0%D1%8F-%D0%B8%D0%BD%D1%84%D0%BE%D1%80%D0%BC%D0%B0%D1%86%D0%B8%D1%8F-%D0%BE-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85)  
[3. Этапы работы над проектом](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D1%8D%D1%82%D0%B0%D0%BF%D1%8B-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B-%D0%BD%D0%B0%D0%B4-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%BE%D0%BC)  


### Описание проекта    
Дано два csv-файла с данными о клиентах [customer.csv](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/CSV%20files/customer.csv) и их транзакциях [transaction.csv](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/CSV%20files/transaction.csv).
Необходимо выполнить следующее:
Создать таблицы со следующими структурами и загрузить данные из csv-файлов.
Выполнить следующие запросы:
1. Вывести все уникальные бренды, у которых стандартная стоимость выше 1500 долларов. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/1.png)
2. Вывести все подтвержденные транзакции за период '2017-04-01' по '2017-04-09' включительно. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/2.png)
3. Вывести все профессии у клиентов из сферы IT или Financial Services, которые начинаются с фразы 'Senior'. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/3.png)
4. Вывести все бренды, которые закупают клиенты, работающие в сфере Financial Services [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/4.png)
5. Вывести 10 клиентов, которые оформили онлайн-заказ продукции из брендов 'Giant Bicycles', 'Norco Bicycles', 'Trek Bicycles'. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/5.png)
6. Вывести всех клиентов, у которых нет транзакций. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/6.png)
7. Вывести всех клиентов из IT, у которых транзакции с максимальной стандартной стоимостью. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/7.png)
8. Вывести всех клиентов из сферы IT и Health, у которых есть подтвержденные транзакции за период '2017-07-07' по '2017-07-17'. [Результат](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Results/8.png)

В процессе работы используется СУБД PostgreSQl, программное приложение SQL DBeaver и  сайт для отрисовки структуры базы данных dbdiagram.io.

:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)


### Краткая информация о данных
Таблица [transaction](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/CSV%20files/transaction.csv) содержит следующие атрибуты:
1. transaction_id;
2. product_id;
3. customer_id;
4. transaction_date;
5. online_order;
6. order_status;
7. brand;
8. product_line;
9. product_class;
10. product_size;
11. list_price;
12. standard_cost.

Таблица [customer](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/CSV%20files/customer.csv) содержит следующие атрибуты:
1. customer_id;
2. first_name;
3. last_name;
4. gender;
5. DOB;
6. job_title;
7. job_industry_category;
8. wealth_segment;
9. deceased_indicator;
10. owns_car;
11. address;
12. postcode;
13. state;
14. country;
15. property_valuation.

[Отрисованный образец структуры базы данных](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/Scheme.pdf)


:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)


### Этапы работы над проектом  
1. Создание таблиц в программе DBeaver:

[SQL скрипты для создания базы данных](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/SQL%20CREATE%20%D1%81%D0%BA%D1%80%D0%B8%D0%BF%D1%82%D1%8B%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.txt)

2. Загрузка данных:

Данные были загружены с помощью функции import в программе DBeaver.

:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Homework%202#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)

3. Вывод необходимой информации с помощью [SQL скриптов](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Homework%202/SQL%20SELECT%20%D1%81%D0%BA%D1%80%D0%B8%D0%BF%D1%82%D1%8B%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.txt)

*В задачах, где необходимо было вывести данные о клиентах, я выводил ID, имя, фамилию и необходимую категорию, поскольку этих данных достаточно, чтобы идентифицировать каждого клиента и проверить, правильно ли выполнен запрос.*


