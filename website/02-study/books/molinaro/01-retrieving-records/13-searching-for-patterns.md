---
layout: page
title: Поиск по шаблону (LIKE)
description: Поиск по шаблону (LIKE)
keywords: Поиск по шаблону (LIKE)
permalink: /books/molinaro/retrieving_records/searching-for-patterns/
---

# Поиск по шаблону (LIKE)

### Задача

Требуется выбрать строки, соответствующие определенной подстроке или шаблону. Рассмотрим следующий запрос и результирующее множество:

    select e.ename, e.job
    from emp e
    where e.deptno in (10,20);

<br/>

    ENAME      JOB
    ---------- ----------
    SMITH      CLERK
    JONES      MANAGER
    CLARK      MANAGER
    SCOTT      ANALYST
    KING       PRESIDENT
    ADAMS      CLERK
    FORD       ANALYST
    MILLER     CLERK

     8 rows selected

<br/>

Из служащих отделов 10 и 20 требуется выбрать только тех, в имени которых встречается буква "I" или чье название должности заканчивается на "ER".

<br/>
<h3>Решение</h3>

Используйте оператор LIKE в сочетании с оператором подставновки SQL ("%"):

    select e.ename, e.job
    from emp e
    where e.deptno in (10,20)
    and (e.ename like '%I%' or e.job like '%ER');

<br/>

    ENAME      JOB
    ---------- ----------
    SMITH      CLERK
    JONES      MANAGER
    CLARK      MANAGER
    KING       PRESIDENT
    MILLER     CLERK

<br/>
<h3>Обсуждение</h3>

При использовании в операции сопоставления с шаблоном LIKE оператор "%" выбирает любую последовательность символов.

Возвращение любой строки, содержащей "I" (в любом месте), обеспечивается заключением шаблона поиска "I" в операторы "%". Если шаблон поиска не заключенв "%", результаты запроса зависят от местоположения "%". Напрммер, чтобы найти названия должностей, закнаивающиеся на "ER", оператор "%" ставится перед "ER". Если требуется найти все должности, начинающиеся с "ER", "%" должен следовать после "ER".

Для выбора какого-нибудь одного символа предоставляется оператор подчеркивания ("\_"). Например, для выбора сотрудников 10 и 20, у которых предпоследняя буква имени "E".

    select e.ename, e.job
    from emp e
    where e.deptno in (10,20)
    and (e.ename like '%E_');

<br/>

    ENAME      JOB
    ---------- ----------
    JONES      MANAGER
    MILLER     CLERK
