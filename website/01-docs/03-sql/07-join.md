---
layout: page
title: Выборка данных из нескольких таблиц (JOIN)
description: Выборка данных из нескольких таблиц (JOIN)
keywords: Выборка данных из нескольких таблиц, JOIN
permalink: /sql/join/
---

# Выборка данных из нескольких таблиц (JOIN)

Довольно часто приходится выбирать данные из нескольких таблиц. Для показа в одном запросе данных из нескольких таблиц Oracle позволяет выполнять так называемые соединения таблиц. Имеется два относящихся к соединению таблиц правила, о которых следует постоянно помнить. Данные из двух (или нескольких) таблиц могут быть объединены в том случае, если у обеих таблиц имеется совпадающий столбец (с тем же самым или с другим именем) и этот столбец в одной из таблиц является первичным ключом (или частью этого ключа).

<table>
<tr>

<td>

SELECT ename, deptno
FROM emp
ORDER BY deptno;

</td>
<td>

SELECT deptno, dname
FROM dept
ORDER BY deptno;

</td>
</tr>

<tr>
<td valign="top">

 <TABLE BORDER="1">
<TR><TH>ENAME</TH><TH>DEPTNO</TH></TR>
<TR><TD>CLARK</TD><TD>10</TD></TR>
<TR><TD>KING</TD><TD>10</TD></TR>
<TR><TD>MILLER</TD><TD>10</TD></TR>
<TR><TD>JONES</TD><TD>20</TD></TR>
<TR><TD>FORD</TD><TD>20</TD></TR>
<TR><TD>ADAMS</TD><TD>20</TD></TR>
<TR><TD>SMITH</TD><TD>20</TD></TR>
<TR><TD>SCOTT</TD><TD>20</TD></TR>
<TR><TD>WARD</TD><TD>30</TD></TR>
<TR><TD>TURNER</TD><TD>30</TD></TR>
<TR><TD>ALLEN</TD><TD>30</TD></TR>
<TR><TD>JAMES</TD><TD>30</TD></TR>
<TR><TD>BLAKE</TD><TD>30</TD></TR>
<TR><TD>MARTIN</TD><TD>30</TD></TR>
</TABLE>

</td>
<td valign="top">

<TABLE BORDER="1">
<TR><TH>DEPTNO</TH><TH>DNAME</TH></TR>
<TR><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>40</TD><TD>OPERATIONS</TD></TR>
</TABLE>

</td>
</tr>

</table>

Давайте рассмотрим пример оператора соединения (join), использующего традиционный синтаксис Oracle, где мы объединяем вместе содержимое таблиц emp и dept для получения перечня всех сотрудников и названий отделов, где они работают:

    SELECT e.ename, e.deptno, d.dname
    FROM emp e, dept d
    WHERE e.deptno = d.deptno;

<TABLE BORDER="1">
<TR><TH>ENAME</TH><TH>DEPTNO</TH><TH>DNAME</TH></TR>
<TR><TD>CLARK</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>KING</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>MILLER</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>JONES</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>FORD</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>ADAMS</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>SMITH</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>SCOTT</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>WARD</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>TURNER</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>ALLEN</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>JAMES</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>BLAKE</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>MARTIN</TD><TD>30</TD><TD>SALES</TD></TR>
</TABLE>

Обратите внимание на многие важные компоненты этого соединения таблиц. Использование во фразе FROM двух таблиц четко указывает на то, что имеет место соединиения таблиц. Обратите также внимание на то, что перед именем каждой таблицы присутствует буква: e для таблицы emp или d для таблицы dept. Это служит иллюстрацией интересной концепции – столбцы могут иметь псевдонимы точно так же, как их имеют таблицы. Псевдонимы служат важной цели – они не дают Oracle запутаться в том, какую таблицу использовать при выводе данных в столбец deptno. Вспомните, что в обеих таблицах (emp и dept) имеются столбцы с именем deptno.

Неоднозначности при соединении таблиц можно также избежать, если в качестве префикса перед именем столбца указать имена таблиц.

    SELECT emp.ename, emp.deptno, dept.dname
    FROM emp, dept
    WHERE emp.deptno = dept.deptno;

Заметьте, что в нашу фразу WHERE включено сравнение по полю deptno, соединяющему данные в emp с данными в dept. В случае отсутствия этой связи в выходные данные были вы включены все данные из emp и dept.

<br/>
<h3>Синтаксис соединения по ANSI/ISO</h3>

В соответствии с синтаксисом ANSI/ISO, для того, чтобы соединить содержимое двух таблиц для получения единого результата, мы должны включить в SQL-оператор фразу JOIN имя*таблицы ON условие*соединения. Если вы хотите в соответствии с этим синтаксисом выполнить то же соединение таблиц, которое мы делали раньше, наш оператор будет выглядеть следующим образом:

<br/><br/>

    SELECT ename, emp.deptno, dname
    FROM emp JOIN dept
    ON emp.deptno = dept.deptno;

<br/><br/>

<TABLE BORDER="1">
<TR><TH>ENAME</TH><TH>DEPTNO</TH><TH>DNAME</TH></TR>
<TR><TD>CLARK</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>KING</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>MILLER</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>JONES</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>FORD</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>ADAMS</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>SMITH</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>SCOTT</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>WARD</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>TURNER</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>ALLEN</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>JAMES</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>BLAKE</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>MARTIN</TD><TD>30</TD><TD>SALES</TD></TR>
</TABLE>

<br/><br/>

Обратите внимание на различия между этим синтаксисом и синтаксисом Oracle. Во-первых, в синтаксисе ANSI/ISO сравнения, используемые для соединения, отделяются от всех остальных сравнений с помощью специального ключевого слова ON, указывающего на то, что именно это сравнение используется для соединения. Вы по-прежнему можете включать в соответствующие ANSI/ISO запросы на соединение фразу WHERE. Единственное отличие состоит в том, что фраза WHERE теперь будет содержать только дополнительные операторы сравнения, используемые дл дополнительной фильтрации данных. Кроме того, вы не должны теперь указывать во фразе FROM имена всех объединяемых таблиц. Вместо этого сразу же после фразы FROM вы должны использовать фразу JOIN, в которой и будут определены имена всех соединяемых таблиц.

<br/>
<h3>Естественные соединения  (NATURAL JOIN)</h3>

Естественным соединением называется соединение между двумя таблицами, в котором Oracle соединяет таблицы по одинаково называющемуся столбцу (столбцам) обеих таблиц (естественным образом!). Естественное соединение выполняется в том случае, если указано ключевое слово NATURAL.

Единственным совпадающим столбцом для таблиц emp и dept является столбец depnto,

    SELECT ename, deptno, dname
    FROM emp NATURAL JOIN dept
    ORDER BY deptno;

<br/>

<TABLE BORDER="1">
<TR><TH>ENAME</TH><TH>DEPTNO</TH><TH>DNAME</TH></TR>
<TR><TD>CLARK</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>KING</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>MILLER</TD><TD>10</TD><TD>ACCOUNTING</TD></TR>
<TR><TD>JONES</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>FORD</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>ADAMS</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>SMITH</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>SCOTT</TD><TD>20</TD><TD>RESEARCH</TD></TR>
<TR><TD>WARD</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>TURNER</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>ALLEN</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>JAMES</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>BLAKE</TD><TD>30</TD><TD>SALES</TD></TR>
<TR><TD>MARTIN</TD><TD>30</TD><TD>SALES</TD></TR>
</TABLE>

Нетрудно заменить, что естественные соединения позволяют в значительной степени упростить запросы с соединением за счет устранения псевдонимов таблиц и сравнений дл соединения.
