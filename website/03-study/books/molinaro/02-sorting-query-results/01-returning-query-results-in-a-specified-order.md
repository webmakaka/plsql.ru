---
layout: page
title: Возвращение результатов запроса в заданном порядке (ORDER BY)
description: Возвращение результатов запроса в заданном порядке (ORDER BY)
keywords: Возвращение результатов запроса в заданном порядке (ORDER BY)
permalink: /books/molinaro/sorting-query-results/returning-query-results-in-a-specified-order/
---

# Возвращение результатов запроса в заданном порядке (ORDER BY)

### Задача

Требуется представить имена, должности и заработные платы служащих 10-го отдела и упорядочить их согласн заработным платам (от наименьшей к наибольшей).

<br/>

### Решение

Используйте оператор ORDER BY:

```
select e.ename, e.job, e.sal
from emp e
where 1=1
and e.deptno =  10
order by e.sal asc;
```

<br/>

```
ENAME      JOB        SAL
---------- ---------- ---
MILLER     CLERK      1300
CLARK      MANAGER    2450
KING       PRESIDENT  5000
```

<br/>

### Обсуждение

Оператор ORDER BY позволяет упорядочивать строки результирующего множества. В нашем примере строки сортируются по столбцу SAL в возрастающем порядке. По умолчанию ORDER BY осуществляет сортировку по возрастанию, поэтому оператор ASC является необязательным. Чтобы обеспечить сортировку по убыванию, используется оператор DESC.

<br/>

```
select e.ename, e.job, e.sal
from emp e
where 1=1
and e.deptno =  10
order by e.sal desc;
```

<br/>

```
ENAME      JOB        SAL
---------- ---------- ---
KING       PRESIDENT  5000
CLARK      MANAGER    2450
MILLER     CLERK      1300
```

Имя столбца, по которому должна проводиться сортировка, задавать необязательно. Можно указать порядковый номер столбца. нумерация столбцов в списе оператора SELECT начинавется с 1 и осуществляется в направлении слева направо. Например:

```
select e.ename, e.job, e.sal
from emp e
where 1=1
and e.deptno =  10
order by 3 desc;
```

<br/>

```
ENAME      JOB        SAL
---------- ---------- ---
KING       PRESIDENT  5000
CLARK      MANAGER    2450
MILLER     CLERK      1300
```

Число 3 в операторе ORDER BY данного примера соответствует третьему столбцу списка оператора SELECT, т.е. столбцу SAL.
