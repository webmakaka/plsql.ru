---
layout: page
title: Конкатенация значений столбцов
description: Конкатенация значений столбцов
keywords: Конкатенация значений столбцов
permalink: /books/molinaro/retrieving_records/concatenating-column-values/
---

# Конкатенация значений столбцов

<h3>Задача</h3>

Требуется извлечь значения нескольких столбцов в одни столбец. Например, в результате запроса к таблице EMP
необходимо получить следующий результат:

    CLARK WORKS AS A MANAGER
    KING WORKS AS A PRESIDENT
    MILLER WORKS AS A CLERK

Однако данные, формирующие это результирующее множество, располагаются в таблице EMP в двух разных столбцах, ENAME и JOB.

    select e.ename, e.job
    from emp e
    where e.deptno = 10

<br/>

    ENAME      JOB
    ---------- ----------
    CLARK      MANAGER
    KING       PRESIDENT
    MILLER     CLERK

<h3>Решение</h3>

Оператором конкатенации для баз данных Oracle является двойная вертикальная черта:

    select e.ename || ' WORKS AS A '|| e.job
    from emp e
    where e.deptno = 10

<br/>

    E.ENAME||'WORKSASA'||E.JOB
    --------------------------------
    CLARK WORKS AS A MANAGER
    KING WORKS AS A PRESIDENT
    MILLER WORKS AS A CLERK

<h3>Обсуждение</h3>

Используйте функцию CONCAT для конкатенации значений нескольких столбцов. Оператор \|\| является сокращенной записью функии CONCAT в Oracle.
