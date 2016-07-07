---
layout: page
title: SQL Практическое занятие 3
permalink: /docs/practice/spec/sql/3/
---

### Практическое занятие 3

1\. Напишите запрос для вывода текущей даты. Назовите столбец Date

    SELECT sysdate as "Date"
    FROM dual;

<br/>

    Date                          
    -------------------------------
    06-JUL-16     



2\. Отделу HR требуется отчет, в котором приводится номер служащего, его фамилия, оклад и новый оклад, повышенный на 15.5% и округленный до целого. Столбец в отчете, содержащий новый оклад, должен иметь имя New Salary.


    SELECT EMPLOYEE_ID, LAST_NAME, SALARY, TRUNC(salary + (salary * 15.5 / 100 ), 0) as "New Salary"
    FROM employees;

<br/>


    EMPLOYEE_ID LAST_NAME                     SALARY New Salary
    ----------- ------------------------- ---------- ----------
            100 King                         24000.9      27721
            101 Kochhar                        17000      19635
            102 De Haan                        17000      19635
            103 Hunold                          9000      10395

            ***

            203 Mavris                          6500       7507
            204 Baer                           10000      11550
            205 Higgins                        12008      13869
            206 Gietz                         998300    1153036

     107 rows selected



4\.	Добавьте еще один столбец, который будет содержать результат вычитания старого оклада из нового. Назовите столбец Increase.

    SELECT EMPLOYEE_ID, LAST_NAME, SALARY, TRUNC(salary + (salary * 15.5 / 100 ), 0) as "New Salary", TRUNC((TRUNC(salary + (salary * 15.5 / 100 ), 0) - salary), 0) as "Increase"
    FROM employees;

<br/>

EMPLOYEE_ID LAST_NAME                     SALARY New Salary   Increase
----------- ------------------------- ---------- ---------- ----------
        100 King                         24000.9      27721       3720
        101 Kochhar                        17000      19635       2635
        102 De Haan                        17000      19635       2635
        103 Hunold                          9000      10395       1395

        ***

        204 Baer                           10000      11550       1550
        205 Higgins                        12008      13869       1861
        206 Gietz                         998300    1153036     154736

 107 rows selected

<br/>

5\.	Выведите фамилии служащих (первая буква каждой фамилии должна быть заглавной, а остальные - строчными) и длину каждой фамилии для тех служащих,  фамилия которых начинается с символа J, A или M. Присвойте соответствующие заголовки столбцам. Отсортируйте результат по фамилиям служащих.

    SELECT INITCAP(LAST_NAME) as "Last Name", LENGTH(LAST_NAME) as "Length"
    FROM employees
    WHERE INSTR(last_name, 'A') = 1
    OR INSTR(last_name, 'M') = 1
    OR INSTR(last_name, 'J') = 1
    ORDER BY LAST_NAME;


<br/>


    Last Name                     Length
    ------------------------- ----------
    Abel                               4
    Ande                               4
    Atkinson                           8
    Austin                             6
    Johnson                            7
    Jones                              5
    Mallin                             6
    Markle                             6
    Marlow                             6
    Marvins                            7
    Matos                              5
    Mavris                             6
    Mccain                             6
    Mcewen                             6
    Mikkilineni                       11
    Mourgos                            7

     16 rows selected


<br/>

6\. Отделу HR необходимы сведения о продолжительности работы служащих. Для каждого служащего выведите фамилию и вычислите количество месяцев со дня найма до настоящего времени, округленное до ближайшего целого. Назовите столбец MONTHS_WORKED. Результаты отсортируйте по количеству отработанных месяцев.


    SELECT LAST_NAME as "Last Name", ROUND(MONTHS_BETWEEN(sysdate, HIRE_DATE)) as "MONTHS_WORKED"
    FROM employees
    ORDER BY MONTHS_WORKED DESC;

<br/>


    Last Name                                           MONTHS_WORKED
    ------------------------- ---------------------------------------
    De Haan                                                       186
    Higgins                                                       169
    Gietz                                                         169
    Mavris                                                        169
    Baer                                                          169

    ***

    Marvins                                                       101
    Lee                                                           100
    Markle                                                        100
    Ande                                                           99
    Kumar                                                          99
    Banda                                                          99

     107 rows selected




7\. Создайте запрос, показывающий фамилию и зарплату сотрудников. Назовите выходной столбец SALARY. Длина столбца SALARY – 15 символов с дополненными слева символами $.

ХЗ как делать.

TODO:

8\. Напишите запрос для отображения первых восьми букв фамилий сотрудников и их заработной платы в виде гистограммы, состоящей из звездочек. Каждая звездочка означает 1000$. Строки должны быть отсортированы по заработной плате в убывающем порядке. Результат должен быть выведен одним столбцом, озаглавленным как EMPLOYEES_AND_THEIR_SALARIES.


TODO:

9\. Напишите запрос для отображения фамилии сотрудников отдела №90 и количества недель, которые каждый сотрудник проработал в компании. Назовите этот столбец TENURE. Значение необходимо урезать до целого. Отсортируйте записи по столбцу tenure.



    SELECT LAST_NAME as "Last Name", (TRUNC((sysdate - HIRE_DATE) / 7)) as "TENURE"
    FROM employees
    WHERE DEPARTMENT_ID = 90
    ORDER BY "TENURE" DESC;

<br/>

    Last Name                     TENURE
    ------------------------- ----------
    De Haan                          807
    King                             681
    Kochhar                          563
