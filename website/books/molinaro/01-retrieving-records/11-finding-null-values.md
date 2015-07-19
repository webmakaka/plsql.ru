---
layout: page
title: Поиск значений NULL (IS NULL)
permalink: /books/molinaro/retrieving_records/finding-null-values/
---

### Поиск значений NULL (IS NULL)


<h3>Задача</h3>

Требуется найти все строки, имеющие в заданном столбце NULL (неопределенное) занчение.


<h3>Решение</h3>

Чтобы выяснить, является ли значение NULL, необходимо использовать оператор IS NULL.


    select e.*
    from emp e
    where comm is null;


<br/>

    EMPNO ENAME      JOB        MGR HIREDATE  SAL COMM DEPTNO
    ----- ---------- ---------- --- --------- --- ---- ------
     7369 SMITH      CLERK      7902 17-DEC-80 800          20
     7566 JONES      MANAGER    7839 02-APR-81 2975          20
     7698 BLAKE      MANAGER    7839 01-MAY-81 2850          30
     7782 CLARK      MANAGER    7839 09-JUN-81 2450          10
     7788 SCOTT      ANALYST    7566 09-DEC-82 3000          20
     7839 KING       PRESIDENT      17-NOV-81 5000          10
     7876 ADAMS      CLERK      7788 12-JAN-83 1100          20
     7900 JAMES      CLERK      7698 03-DEC-81 950          30
     7902 FORD       ANALYST    7566 03-DEC-81 3000          20
     7934 MILLER     CLERK      7782 23-JAN-82 1300          10


<br/>
<h3>Обсуждение</h3>



NULL никогда не бывает равен или не равен ни одному значению, даже самому себе, поэтому с момощью операторов = или != нельзя определить, равно ли значение NULL или не равно.Для проверки наличия в строке значения NULL должен использоваться оператор IS NULL.

Кроме того, с помощью оператора IS NOT NULL, можно выбрать строки, не содержащие NULL значения в заданном столбце.
