---
layout: page
title: Сортировка смешанных буквенно-цифровых данных (TRANSLATE и REPLACE)
permalink: /books/molinaro/sorting-query-results/sorting-mixed-alphanumeric-data/
---


### Сортировка смешанных буквенно-цифровых данных (TRANSLATE и REPLACE)



<h3>Задача</h3>

Требуется сортировать смешанные буквенно-цифровые данные по числовой или символьной части. Рассмотрим следующее представление:


    create view V
    as
    select e.ename||'  '|| e.deptno as data
    from emp e

<br/>


    select * from V;


<br/>


    DATA
    ----------------------------------------------------
    SMITH  20
    ALLEN  30
    WARD  30
    JONES  20
    MARTIN  30
    BLAKE  30
    CLARK  10
    SCOTT  20
    KING  10
    TURNER  30
    ADAMS  20
    JAMES  30
    FORD  20
    MILLER  10

     14 rows selected



<br/>

<h3>Решение</h3>

Вносим коррективы в строку, подлежащую сортировке,с помощью функции REPLACE (заместить) и TRANSLATE (переместить):


    /* Сортируем по DEPTNO */
    select data
    from V
    order by replace(data,
             replace(
             translate(data, '0123456789', '##########'), '#', ''), '');


<br/>

    DATA
    ----------------------------------------------------
    CLARK  10
    KING  10
    MILLER  10
    JONES  20
    FORD  20
    ADAMS  20
    SMITH  20
    SCOTT  20
    WARD  30
    TURNER  30
    ALLEN  30
    JAMES  30
    BLAKE  30
    MARTIN  30

     14 rows selected


<br/>

    /* Сортируем по ENAME */
    select data
    from V
    order by replace(
             translate(data, '0123456789', '##########'), '#', '');


<br/>


    DATA
    ----------------------------------------------------
    ADAMS  20
    ALLEN  30
    BLAKE  30
    CLARK  10
    FORD  20
    JAMES  30
    JONES  20
    KING  10
    MARTIN  30
    MILLER  10
    SCOTT  20
    SMITH  20
    TURNER  30
    WARD  30

     14 rows selected


<br/>
<h3>Обсуждение</h3>


Функция TRANSLATE и REPLACE удаляют из каждой строки числа или символы соответственно, что обеспечивает возможность сортировки по данным одного или другого типа. Значения, переданные в ORDER BY, показаны в результатах следующего запроса.


    select data
    , replace (data,
        replace (
            translate(data, '0123456789', '##########'), '#', ''),'' ) nums
    , replace (
            translate(data, '0123456789', '##########'), '#', '') chars
    from V;


<br/>


    DATA                                                 NUMS                                                 CHARS
    -------------------
    SMITH  20                                            20                                                   SMITH
    ALLEN  30                                            30                                                   ALLEN
    WARD  30                                             30                                                   WARD
    JONES  20                                            20                                                   JONES
    MARTIN  30                                           30                                                   MARTIN
    BLAKE  30                                            30                                                   BLAKE
    CLARK  10                                            10                                                   CLARK
    SCOTT  20                                            20                                                   SCOTT
    KING  10                                             10                                                   KING
    TURNER  30                                           30                                                   TURNER
    ADAMS  20                                            20                                                   ADAMS
    JAMES  30                                            30                                                   JAMES
    FORD  20                                             20                                                   FORD
    MILLER  10                                           10                                                   MILLER

     14 rows selected
