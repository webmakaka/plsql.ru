---
layout: page
title: Сортировка по нескольким полям (ORDER BY)
description: Сортировка по нескольким полям (ORDER BY)
keywords: Сортировка по нескольким полям (ORDER BY)
permalink: /books/molinaro/sorting-query-results/sorting-by-multiple-fields/
---

# Сортировка по нескольким полям (ORDER BY)

### Задача

Требуется сортировать строки таблицы EMP сначала по стобцу DEPTNO по возрастанию, а затем по заработным платам по убыванию.

<br/>

### Решение

В операторе ORDER BY через запятую перечислите столбцы, по которым должна проводиться сортировка:

<br/>

```
select e.empno, e.deptno, e.sal, e.ename, e.job
from emp e
order by e.deptno, e.sal desc;
```

<br/>

```
EMPNO DEPTNO SAL ENAME      JOB
----- ------ --- ---------- ----------
    7839     10 5000 KING       PRESIDENT
    7782     10 2450 CLARK      MANAGER
    7934     10 1300 MILLER     CLERK
    7788     20 3000 SCOTT      ANALYST
    7902     20 3000 FORD       ANALYST
    7566     20 2975 JONES      MANAGER
    7876     20 1100 ADAMS      CLERK
    7369     20 800 SMITH      CLERK
    7698     30 2850 BLAKE      MANAGER
    7499     30 1600 ALLEN      SALESMAN
    7844     30 1500 TURNER     SALESMAN
    7654     30 1250 MARTIN     SALESMAN
    7521     30 1250 WARD       SALESMAN
    7900     30 950 JAMES      CLERK

    14 rows selected
```

<br/>

### Обсуждение

Старшинство столбцов, по которым осуществляется сортировка, в операторе ORDER BY определяется слева направо. Если столбце задается его порябковым номером в списке оператора SELECT, то это число не должно превышать количества элементов в списке SELECT. Можно проводить сортировку по столбцу, не входящему в список SELECT, но для этого необходимо явно указать его имя. Тем не менее, при использовании в запросе операторов GROUP BY или DISTINCT сортировка может осуществляться только по столбцам из списка оператора SELECT.
