---
layout: page
title: Возвращение n случайных записей таблицы
permalink: /books/molinaro/retrieving_records/returning-n-random-records-from-a-table/
---

### Возвращение n случайных записей таблицы



<h3>Задача</h3>

Требуется возвратить некоторое число записей таблицы, выбранных случайным образом. Необходимо так изменить следующее выражение, чтобы при каждом последующем выполнении оно возвращало разные пять строк:


    select e.ename, e.job
    from emp e



<h3>Решение</h3>

Используйте встроенную функцию VALUE, которая находится во встроенном пакете DBMS_RANDOM, в сочетании с ORDER BY и встроенную функцию ROWNUM:


    select x.*
    from (
          select e.ename, e.job
          from emp e
          order by dbms_random.value()
         ) x
    where rownum <=5


<br/>


    ENAME      JOB
    ---------- ----------
    MILLER     CLERK
    SMITH      CLERK
    KING       PRESIDENT  
    JONES      MANAGER
    TURNER     SALESMAN

    ENAME      JOB
    ---------- ----------
    KING       PRESIDENT  
    ALLEN      SALESMAN
    JAMES      CLERK
    SCOTT      ANALYST
    FORD       ANALYST

<br/>

<h3>Обсуждение</h3>


Происходит сортировка результирующего набора с помощью оператоара ORDER BY и функции dbms_random.value(). После этого происходит ограничение числа возвращаемых строк с помощью функции ROWNUM.

Важно четко различать, что происходит при использовании в ORDER BY функции и числовой константы.
При задании в операторе ORDER BY числовой константы, сортировка осуществляется по столбцу с заданным в списке SELECT порядковым номером. Когда в ORDER BY задается функция, сортировке подвергается результат, возвращаемый функцией для каждой строки.
