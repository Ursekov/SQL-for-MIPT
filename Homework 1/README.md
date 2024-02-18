# [Создание БД](https://github.com/Ursekov/SQL-for-MIPT)

## Оглавление  
[1. Описание проекта](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%B0)  
[2. Краткая информация о данных](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D0%BA%D1%80%D0%B0%D1%82%D0%BA%D0%B0%D1%8F-%D0%B8%D0%BD%D1%84%D0%BE%D1%80%D0%BC%D0%B0%D1%86%D0%B8%D1%8F-%D0%BE-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85)  
[3. Этапы работы над проектом](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D1%8D%D1%82%D0%B0%D0%BF%D1%8B-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B-%D0%BD%D0%B0%D0%B4-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%BE%D0%BC)  
[4. Результаты](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B)    


### Описание проекта    
Дан файл с данными по клиентам и транзакциям: [customer_and_transaction.xlsx](https://github.com/Ursekov/SQL-for-MIPT/blob/master/customer_and_transaction%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.xlsx).
Необходимо выполнить следующие пункты:
1. Продумать структуру базы данных и отрисовать в редакторе.
2. Нормализовать базу данных (1НФ — 3НФ), описав, к какой нормальной форме приводится таблица и почему таблица в этой нормальной форме изначально не находилась.
3. Создать все таблицы в DBeaver, указав первичные ключи к таблицам, правильные типы данных, могут ли поля быть пустыми или нет (использовать команду CREATE TABLE).
4. Загрузить данные в таблицы в соответствии с созданной структурой (использовать команду INSERT INTO или загрузить файлы, используя возможности инструмента DBeaver; в случае загрузки файлами приложить скрины, что данные действительно были залиты).

В процессе работы используется СУБД PostgreSQl, программное приложение SQL DBeaver и  сайт для отрисовки структуры базы данных dbdiagram.io.

:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)


### Краткая информация о данных
Данные изначально разбиты на две таблицы (transaction, customer).

Таблица transaction содержит следующие атрибуты:
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

Таблица customer содержит следующие атрибуты:
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

[Отрисованный образец изначальной структуры базы данных](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Scheme/V%201.pdf)


:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)


### Этапы работы над проектом  
1. Нормализация данных:

    1.1. Данные уже находятся в первой нормальной форме, поскольку все атрибуты в таблице простые, все сохраняемые данные на пересечении столбцов и строк — содержат лишь скалярные значения.
    
    1.2. Данные не находятся во второй нормальной форме, поскольку описание продукта в таблице transaction не относятся к первичному ключу данной таблице, в связи с чем, данные о продукте были перемещены в таблицу product, а в таблице transaction был создан суррогатный ключ, с помощью которого можно ссылаться на записи в таблице product. Суррогатный ключ был создан в связи с тем, что изначальный product_id не подходил для описания всех продуктов, поскольку в рамках одного продукта, можно было выбрать, к примеру, разный product_class, что меняло цену товара. [Отрисованный образец структуры базы данных](https://github.com/Ursekov/SQL-for-MIPT/blob/master/Scheme/V%202.pdf)
    
    1.3. Данные находятся в третьей нормальной форме, поскольку все атрибуты зависят лишь от перичного ключа.

2. Создание таблиц в программе DBeaver:

[SQL скрипты для создания базы данных](https://github.com/Ursekov/SQL-for-MIPT/blob/master/SQL%20%D1%81%D0%BA%D1%80%D0%B8%D0%BF%D1%82%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.txt)

3. Загрузка данных:

Данные были загружены с помощью функции import в программе DBeaver. Для каждой таблицы, были созданы файлы CSV формата ([transaction](https://github.com/Ursekov/SQL-for-MIPT/blob/master/CSV%20files/Transaction%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.csv), [product](https://github.com/Ursekov/SQL-for-MIPT/blob/master/CSV%20files/Product%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.csv), [customer](https://github.com/Ursekov/SQL-for-MIPT/blob/master/CSV%20files/Customer%20%D0%A3%D1%80%D1%81%D0%B5%D0%BA%D0%BE%D0%B2%20%D0%90%D0%90.csv))


:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)


### Результаты:  
Скрины из DBeaver с информацией о таблицах находятся в папке [Results](https://github.com/Ursekov/SQL-for-MIPT/tree/master/Results) в данном репозитории.

:arrow_up:[к оглавлению](https://github.com/Ursekov/SQL-for-MIPT?tab=readme-ov-file#%D0%BE%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)