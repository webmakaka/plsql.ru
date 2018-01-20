---
layout: page
title: SQL Практическое занятие 2
permalink: /practice/spec/sql/2/
---

### Практическое занятие 2

**Отделу HR необходима помощь в создании некоторых запросов**


1\. Вследствие проблем финансирования отделу HR необходим отчет, в котором показываются фамилии и оклады служащих, получающих более $12,000.

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


<br/>

Выведите фамилию и номер отдела всех служащих из отделов 20 и 50. Отсортируйте данные по фамилиям в алфавитном порядке.


    SELECT last_name, department_id
    FROM employees
    WHERE department_id in (20, 50)
    ORDER BY last_name;

<br/>


    LAST_NAME                 DEPARTMENT_ID
    ------------------------- -------------
    Atkinson                             50
    Bell                                 50
    Bissot                               50
    Bull                                 50
    Cabrio                               50
    Chung                                50
    Davies                               50
    Dellinger                            50
    Dilly                                50
    Everett                              50
    Fay                                  20
    Feeney                               50
    Fleaur                               50
    Fripp                                50
    Gates                                50
    Gee                                  50
    Geoni                                50
    Grant                                50
    Hartstein                            20
    Jones                                50
    Kaufling                             50
    Ladwig                               50
    Landry                               50
    Mallin                               50
    Markle                               50
    Marlow                               50
    Matos                                50
    McCain                               50
    Mikkilineni                          50
    Mourgos                              50
    Nayer                                50
    OConnell                             50
    Olson                                50
    Patel                                50
    Perkins                              50
    Philtanker                           50
    Rajs                                 50
    Rogers                               50
    Sarchand                             50
    Seo                                  50
    Stiles                               50
    Sullivan                             50
    Taylor                               50
    Vargas                               50
    Vollman                              50
    Walsh                                50
    Weissgbgg                            50

     47 rows selected


<br/>

Вывести фамилии и оклады служащих отделов 20 и 50, зарабатывающих от $5000 до $12,000. Назовите столбцы Employee и Monthly Salary, соответственно.


<br/>

    SELECT last_name as Employee, salary as "Monthly Salary"
    FROM employees
    WHERE 1=1
        and department_id in (20, 50)
        and (salary >= 5000 and salary <= 12000);


<br/>

    EMPLOYEE                  Monthly Sa
    ------------------------- ----------
    Weissgbgg                       8000
    Fripp                           8200
    Kaufling                        7900
    Vollman                         6500
    Mourgos                         5800
    Fay                             6000

     6 rows selected


Отделу HR необходим отчет, в котором выводятся фамилии и даты найма всех служащих, нанятых в 2004 г

    SELECT last_name, hire_date
    FROM employees
    WHERE hire_date
               BETWEEN TO_DATE ('01.01.2004', 'dd.mm.yyyy')
                   AND TO_DATE ('31.12.2004', 'dd.mm.yyyy');

<br/>

    LAST_NAME                 HIRE_DATE                     
    ------------------------- -------------------------------
    Weissgbgg                 18-JUL-04                      
    Mallin                    14-JUN-04                      
    Russell                   01-OCT-04                      
    King                      30-JAN-04                      
    Sully                     04-MAR-04                      
    McEwen                    01-AUG-04                      
    Abel                      11-MAY-04                      
    Sarchand                  27-JAN-04                      
    Bell                      04-FEB-04                      
    Hartstein                 17-FEB-04                      

     10 rows selected

<br/>

Создайте отчет, содержащий фамилии и должности всех служащих, не имеющих менеджера.

    SELECT last_name, job_id
    FROM employees
    WHERE manager_id is null;

<br/>

    LAST_NAME                 JOB_ID   
    ------------------------- ----------
    King                      AD_PRES   


<br/>

Создайте отчет для вывода фамилий, окладов и комиссионные всех служащих, зарабатывающих комиссионные. Отсортируйте данные в порядке убывания окладов и комиссионных.


    SELECT last_name, salary, COMMISSION_PCT
    FROM employees
    WHERE COMMISSION_PCT is not null
    ORDER BY salary desc, COMMISSION_PCT desc;

<br/>

    LAST_NAME                     SALARY COMMISSION_PCT
    ------------------------- ---------- --------------
    Russell                        14000             .4
    Partners                       13500             .3
    Errazuriz                      12000             .3
    Ozer                           11500            .25
    Cambrault                      11000             .3
    Abel                           11000             .3
    Vishney                        10500            .25
    Zlotkey                        10500             .2
    King                           10000            .35
    Tucker                         10000             .3
    Bloom                          10000             .2
    Fox                             9600             .2
    Sully                           9500            .35
    Bernstein                       9500            .25
    Greene                          9500            .15
    McEwen                          9000            .35
    Hall                            9000            .25
    Hutton                          8800            .25
    Taylor                          8600             .2
    Livingston                      8400             .2
    Smith                           8000             .3
    Olsen                           8000             .2
    Doran                           7500             .3
    Cambrault                       7500             .2
    Smith                           7400            .15
    Bates                           7300            .15
    Marvins                         7200             .1
    Sewall                          7000            .25
    Tuvault                         7000            .15
    Grant                           7000            .15
    Lee                             6800             .1
    Ande                            6400             .1
    Banda                           6200             .1
    Johnson                         6200             .1
    Kumar                           6100             .1

     35 rows selected


<br/>

Сотрудникам отдела HR требуются запросы с более гибкими возможностями. Так необходим отчет, в котором показываются фамилии и оклады служащих, зарабатывающих больше некоторой величины, вводимой пользователем после приглашения. (Можете изменить запрос, созданный при выполнении задания 1.) Запишите запрос в файл lab_02_10.sql. Ниже приводятся результаты, которые получаются, когда после приглашения вводится 12000

    Впадлу делать такие запросы. Реально мне никогда такого рода функционал не был нужен.

Отделу HR необходимы отчеты по каждому менеджеру. Создайте отчет, при выполнении которого запрашивается идентификатор менеджера (manager_ID) и выводятся следующие сведения о подчиняющихся ему сотрудниках: табельный номер, фамилия и номер отдела. Должна быть предоставлена возможность отсортировать результаты на основе заданного столбца.

    Впадлу делать такие запросы. Реально мне никогда такого рода функционал не был нужен.


<br/>

Выведите все фамилии служащих, в которых третья буква – a


    SELECT last_name
    FROM employees
    WHERE instr(last_name, 'a') = 3;

<br/>

    LAST_NAME               
    -------------------------
    Grant                    
    Grant                    
    Whalen  

<br/>

Выведите все фамилии служащих, в которых есть буквы “a” и “e”.


    SELECT last_name
    FROM employees
    WHERE instr(last_name, 'a') != 0 OR instr(last_name, 'e') != 0

<br/>

    LAST_NAME               
    -------------------------
    Abel                     
    Ande                     
    Baer                     
    Baida                    
    Banda                    
    Bates                    
    Bell                     
    Bernstein                
    Cabrio                   
    Cambrault                
    Cambrault                
    Chen                     
    Colmenares               
    Davies                   
    De Haan                  
    Dellinger                
    Doran                    
    Errazuriz                
    Everett                  
    Faviet                   
    Fay                      
    Feeney                   
    Fleaur                   
    Gates                    
    Gee                      
    Geoni                    
    Gietz                    
    Grant                    
    Grant                    
    Greenberg                
    Greene                   
    Hall                     
    Hartstein                
    Jones                    
    Kaufling                 
    Kochhar                  
    Kumar                    
    Ladwig                   
    Landry                   
    Lee                      
    Lorentz                  
    Mallin                   
    Markle                   
    Marlow                   
    Marvins                  
    Matos                    
    Mavris                   
    McCain                   
    McEwen                   
    Mikkilineni              
    Nayer                    
    OConnell                 
    Olsen                    
    Ozer                     
    Partners                 
    Pataballa                
    Patel                    
    Perkins                  
    Philtanker               
    Rajs                     
    Raphaely                 
    Rogers                   
    Russell                  
    Sarchand                 
    Sciarra                  
    Seo                      
    Sewall                   
    Stiles                   
    Sullivan                 
    Taylor                   
    Taylor                   
    Tobias                   
    Tucker                   
    Tuvault                  
    Urman                    
    Vargas                   
    Vishney                  
    Vollman                  
    Walsh                    
    Weissgbgg                
    Whalen                   
    Zlotkey                  

     82 rows selected


<br/>

Запросите фамилии, должности и оклады всех служащих, работающих торговыми представителя (SA_REP) или клерками на складе (ST_CLERK), у которых оклад не может быть равен $2500,  $3500 или $7000.

<br/>

    SELECT last_name, job_id, salary
    FROM employees
    WHERE job_id in ('SA_REP', 'ST_CLERK')
    and salary not in (2500, 3500, 7000)

<br/>

    LAST_NAME                 JOB_ID         SALARY
    ------------------------- ---------- ----------
    Nayer                     ST_CLERK         3200
    Mikkilineni               ST_CLERK         2700
    Landry                    ST_CLERK         2400
    Markle                    ST_CLERK         2200
    Bissot                    ST_CLERK         3300
    Atkinson                  ST_CLERK         2800
    Olson                     ST_CLERK         2100
    Mallin                    ST_CLERK         3300
    Rogers                    ST_CLERK         2900
    Gee                       ST_CLERK         2400
    Philtanker                ST_CLERK         2200
    Ladwig                    ST_CLERK         3600
    Stiles                    ST_CLERK         3200
    Seo                       ST_CLERK         2700
    Davies                    ST_CLERK         3100
    Matos                     ST_CLERK         2600
    Tucker                    SA_REP          10000
    Bernstein                 SA_REP           9500
    Hall                      SA_REP           9000
    Olsen                     SA_REP           8000
    Cambrault                 SA_REP           7500
    King                      SA_REP          10000
    Sully                     SA_REP           9500
    McEwen                    SA_REP           9000
    Smith                     SA_REP           8000
    Doran                     SA_REP           7500
    Vishney                   SA_REP          10500
    Greene                    SA_REP           9500
    Marvins                   SA_REP           7200
    Lee                       SA_REP           6800
    Ande                      SA_REP           6400
    Banda                     SA_REP           6200
    Ozer                      SA_REP          11500
    Bloom                     SA_REP          10000
    Fox                       SA_REP           9600
    Smith                     SA_REP           7400
    Bates                     SA_REP           7300
    Kumar                     SA_REP           6100
    Abel                      SA_REP          11000
    Hutton                    SA_REP           8800
    Taylor                    SA_REP           8600
    Livingston                SA_REP           8400
    Johnson                   SA_REP           6200

     43 rows selected

<br/>

Получить фамилии, оклады и комиссионные всех служащих, у которых комиссионные составляют 20%

    SELECT last_name, salary, COMMISSION_PCT
    FROM employees
    WHERE COMMISSION_PCT = 0.2;

<br/>

    LAST_NAME                     SALARY COMMISSION_PCT
    ------------------------- ---------- --------------
    Zlotkey                        10500             .2
    Olsen                           8000             .2
    Cambrault                       7500             .2
    Bloom                          10000             .2
    Fox                             9600             .2
    Taylor                          8600             .2
    Livingston                      8400             .2

     7 rows selected
