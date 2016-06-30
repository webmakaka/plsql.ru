---
layout: page
title: SQL Практическое занятие 2
permalink: /docs/practice/spec/sql/2/
---


**Отделу HR необходима помощь в создании некоторых запросов**


1. Вследствие проблем финансирования отделу HR необходим отчет, в котором показываются фамилии и оклады служащих, получающих более $12,000.

    SELECT last_name, salary
    FROM employees
    WHERE salary > 12000;

<br/>


    LAST_NAME                     SALARY
    ------------------------- ----------
    King                         24000.9
    Kochhar                        17000
    De Haan                        17000
    Greenberg                      12008
    Russell                        14000
    Partners                       13500
    Hartstein                      13000
    Higgins                        12008
    Gietz                         998300

     9 rows selected

<br/>

Создайте запрос для вывода фамилии и номера отдела служащего под номером 176


    SELECT last_name, department_id
    FROM employees
    WHERE employee_id = 176;

<br/>


    LAST_NAME                 DEPARTMENT_ID
    ------------------------- -------------
    Taylor                               80



Отделу HR необходимы данные о высокооплачиваемых и низкооплачиваемых сотрудниках. Выведите фамилии и оклады всех служащих, чей оклад не входит в диапазон от $5000 до $12000.


    SELECT last_name, salary
    FROM employees
    WHERE
    salary < 5000
    or salary > 21000;

<br/>    

    LAST_NAME                     SALARY
    ------------------------- ----------
    King                         24000.9
    Austin                          4800
    Pataballa                       4800
    Lorentz                         4200
    Khoo                            3100
    Baida                           2900
    Tobias                          2800
    Himuro                          2600
    Colmenares                      2500
    Nayer                           3200
    Mikkilineni                     2700
    Landry                          2400
    Markle                          2200
    Bissot                          3300
    Atkinson                        2800
    Marlow                          2500
    Olson                           2100
    Mallin                          3300
    Rogers                          2900
    Gee                             2400
    Philtanker                      2200
    Ladwig                          3600
    Stiles                          3200
    Seo                             2700
    Patel                           2500
    Rajs                            3500
    Davies                          3100
    Matos                           2600
    Vargas                          2500
    Taylor                          3200
    Fleaur                          3100
    Sullivan                        2500
    Geoni                           2800
    Sarchand                        4200
    Bull                            4100
    Dellinger                       3400
    Cabrio                          3000
    Chung                           3800
    Dilly                           3600
    Gates                           2900
    Perkins                         2500
    Bell                            4000
    Everett                         3900
    McCain                          3200
    Jones                           2800
    Walsh                           3100
    Feeney                          3000
    OConnell                        2600
    Grant                           2600
    Whalen                          4400
    Gietz                         998300

     51 rows selected


<br/>  

Создайте отчет для вывода фамилии, идентификатора должности и даты начала работы всех служащих, с фамилиями Matos и Taylor. Отсортируйте данные в порядке возрастания даты найма.


    SELECT last_name, job_id, hire_date
    FROM employees
    WHERE last_name = 'Matos' OR last_name = 'Taylor'
    ORDER BY hire_date ASC;


<br/>


    LAST_NAME                 JOB_ID     HIRE_DATE                     
    ------------------------- ---------- -------------------------------
    Taylor                    SH_CLERK   24-JAN-06                      
    Matos                     ST_CLERK   15-MAR-06                      
    Taylor                    SA_REP     24-MAR-06        
