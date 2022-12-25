---
layout: page
title: Сортировка по подстрокам
description: Сортировка по подстрокам
keywords: Сортировка по подстрокам
permalink: /books/molinaro/sorting-query-results/sorting-by-substrings/
---

# Сортировка по подстрокам

### Задача

Требуется сортировать результаты запроса по частям строки. Напрмер, имена и должности служащих, возвращенные из таблицы EMP, должны быть упорядочены по последним двум символам поля должности.

<br/>

<h3>Решение</h3>

Используйте в операторе ORDER BY функцию SUBSTR:

    select e.ename, e.job
    from emp e
    order by substr(e.job, length(e.job)-2);

<br/>
    ENAME      JOB
    ---------- ----------
    KING       PRESIDENT  
    MILLER     CLERK
    JAMES      CLERK
    ADAMS      CLERK
    SMITH      CLERK
    BLAKE      MANAGER
    JONES      MANAGER
    CLARK      MANAGER
    MARTIN     SALESMAN
    TURNER     SALESMAN
    WARD       SALESMAN
    ALLEN      SALESMAN
    FORD       ANALYST
    SCOTT      ANALYST

     14 rows selected

<br/>

<h3>Обсуждение</h3>

Чтобы сортировать по последним двум символам строки, находим конец строки (что соответствуе ее длине) и вычитаем 2. Таким образом, начальная позиция будет располагаться на предпоследнем символе строки. Теперь выбираем все символы после этой позиции.
