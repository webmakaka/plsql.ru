---
layout: page
title: Сортировка возвращаемых данных (ORDER BY)
description: Сортировка возвращаемых данных (ORDER BY)
keywords: Сортировка возвращаемых данных, ORDER BY
permalink: /sql/order-by/
---

# Сортировка возвращаемых данных (ORDER BY)

По умолчанию Oracle не возвращает запрошенные данные отсортированными. Для того, чтобы упорядочить данные полученные оператором SELECT используют конструкцию ORDER BY.

В этой фразе можно указать порядок сортировки для одного или нескольких столбцов в возрастающем или убывающем порядке для каждого из указанных столбцов. Если для порядка сортировки указано боле одного выражения, Oracle сортирует данные в порядке их появления в первом выражении. Если после этого в выходных данных останутся дубликаты, Oracle сортирует их в порядке, указанном в втором выражении, и так далее. Фраза ORDER BY обычно является последней в операторах языка структурированных запросов. Обычно в синтаксис фразы ORDER BY включаются как сам текст ORDER BY, так и имена столбцов, по которым Oracle должна упорядочить результаты, за каждым из которых может следовать специальная фраза, определяющая направление упорядочивания (asc для упорядочивания по возрастанию и desc для упорядочивания по убыванию). Значением по умолчанию для этой фразы является asc. Ниже приводится пример использования фразы ORDER BY:

<br/>

    SELECT name AS "ФИО", matches AS "Матчи", goals "Голы"
    FROM russian_team
    ORDER BY matches;

<br/>

<TABLE BORDER="1">
<TR><TH>&#1060;&#1048;&#1054;</TH><TH>&#1052;&#1072;&#1090;&#1095;&#1080;</TH><TH>&#1043;&#1086;&#1083;&#1099;</TH></TR>
<TR><TD>&#1057;&#1072;&#1077;&#1085;&#1082;&#1086; &#1048;&#1074;&#1072;&#1085; &#1048;&#1074;&#1072;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>13</TD><TD>9</TD></TR>
<TR><TD>&#1050;&#1086;&#1083;&#1086;&#1076;&#1080;&#1085; &#1044;&#1077;&#1085;&#1080;&#1089; &#1040;&#1083;&#1077;&#1082;&#1089;&#1077;&#1077;&#1074;&#1080;&#1095;</TD><TD>24</TD><TD>0</TD></TR>
<TR><TD>&#1058;&#1086;&#1088;&#1073;&#1080;&#1085;&#1089;&#1082;&#1080;&#1081; &#1044;&#1084;&#1080;&#1090;&#1088;&#1080;&#1081; &#1045;&#1074;&#1075;&#1077;&#1085;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>29</TD><TD>2</TD></TR>
<TR><TD>&#1047;&#1099;&#1088;&#1103;&#1085;&#1086;&#1074; &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; &#1043;&#1077;&#1086;&#1088;&#1075;&#1080;&#1077;&#1074;&#1080;&#1095;</TD><TD>47</TD><TD>7</TD></TR>
<TR><TD>&#1057;&#1099;&#1095;&#1077;&#1074; &#1044;&#1084;&#1080;&#1090;&#1088;&#1080;&#1081; &#1045;&#1074;&#1075;&#1077;&#1085;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>47</TD><TD>14</TD></TR>
<TR><TD>&#1055;&#1072;&#1074;&#1083;&#1102;&#1095;&#1077;&#1085;&#1082;&#1086; &#1056;&#1086;&#1084;&#1072;&#1085; &#1040;&#1085;&#1072;&#1090;&#1086;&#1083;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>20</TD></TR>
<TR><TD>&#1046;&#1080;&#1088;&#1082;&#1086;&#1074; &#1070;&#1088;&#1080;&#1081; &#1042;&#1072;&#1083;&#1077;&#1085;&#1090;&#1080;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>0</TD></TR>
<TR><TD>&#1041;&#1080;&#1083;&#1103;&#1083;&#1077;&#1090;&#1076;&#1080;&#1085;&#1086;&#1074; &#1044;&#1080;&#1085;&#1080;&#1103;&#1088; &#1056;&#1077;&#1085;&#1072;&#1090;&#1086;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>6</TD></TR>
<TR><TD>&#1040;&#1082;&#1080;&#1085;&#1092;&#1077;&#1077;&#1074; &#1048;&#1075;&#1086;&#1088;&#1100; &#1042;&#1083;&#1072;&#1076;&#1080;&#1084;&#1080;&#1088;&#1086;&#1074;&#1080;&#1095;</TD><TD>51</TD><TD>0</TD></TR>
<TR><TD>&#1057;&#1077;&#1084;&#1096;&#1086;&#1074; &#1048;&#1075;&#1086;&#1088;&#1100; &#1055;&#1077;&#1090;&#1088;&#1086;&#1074;&#1080;&#1095;</TD><TD>59</TD><TD>3</TD></TR>
<TR><TD>&#1040;&#1085;&#1102;&#1082;&#1086;&#1074; &#1040;&#1083;&#1077;&#1082;&#1089;&#1072;&#1085;&#1076;&#1088; &#1043;&#1077;&#1085;&#1085;&#1072;&#1076;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>63</TD><TD>1</TD></TR>
<TR><TD>&#1057;&#1077;&#1084;&#1072;&#1082; &#1057;&#1077;&#1088;&#1075;&#1077;&#1081; &#1041;&#1086;&#1075;&#1076;&#1072;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>65</TD><TD>4</TD></TR>
<TR><TD>&#1040;&#1088;&#1096;&#1072;&#1074;&#1080;&#1085; &#1040;&#1085;&#1076;&#1088;&#1077;&#1081; &#1057;&#1077;&#1088;&#1075;&#1077;&#1077;&#1074;&#1080;&#1095;</TD><TD>68</TD><TD>16</TD></TR>
<TR><TD>&#1048;&#1075;&#1085;&#1072;&#1096;&#1077;&#1074;&#1080;&#1095; &#1057;&#1077;&#1088;&#1075;&#1077;&#1081; &#1053;&#1080;&#1082;&#1086;&#1083;&#1072;&#1077;&#1074;&#1080;&#1095;</TD><TD>72</TD><TD>5</TD></TR>
</TABLE>

<br/><br/>

Пример сортировки выходных данных в убывающем порядке с использованием ключевого слова desc:

    SELECT name AS "ФИО", matches AS "Матчи", goals "Голы"
    FROM russian_team
    ORDER BY goals DESC;

<br/>

<TABLE BORDER="1">
<TR><TH>&#1060;&#1048;&#1054;</TH><TH>&#1052;&#1072;&#1090;&#1095;&#1080;</TH><TH>&#1043;&#1086;&#1083;&#1099;</TH></TR>
<TR><TD>&#1055;&#1072;&#1074;&#1083;&#1102;&#1095;&#1077;&#1085;&#1082;&#1086; &#1056;&#1086;&#1084;&#1072;&#1085; &#1040;&#1085;&#1072;&#1090;&#1086;&#1083;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>20</TD></TR>
<TR><TD>&#1040;&#1088;&#1096;&#1072;&#1074;&#1080;&#1085; &#1040;&#1085;&#1076;&#1088;&#1077;&#1081; &#1057;&#1077;&#1088;&#1075;&#1077;&#1077;&#1074;&#1080;&#1095;</TD><TD>68</TD><TD>16</TD></TR>
<TR><TD>&#1057;&#1099;&#1095;&#1077;&#1074; &#1044;&#1084;&#1080;&#1090;&#1088;&#1080;&#1081; &#1045;&#1074;&#1075;&#1077;&#1085;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>47</TD><TD>14</TD></TR>
<TR><TD>&#1057;&#1072;&#1077;&#1085;&#1082;&#1086; &#1048;&#1074;&#1072;&#1085; &#1048;&#1074;&#1072;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>13</TD><TD>9</TD></TR>
<TR><TD>&#1047;&#1099;&#1088;&#1103;&#1085;&#1086;&#1074; &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; &#1043;&#1077;&#1086;&#1088;&#1075;&#1080;&#1077;&#1074;&#1080;&#1095;</TD><TD>47</TD><TD>7</TD></TR>
<TR><TD>&#1041;&#1080;&#1083;&#1103;&#1083;&#1077;&#1090;&#1076;&#1080;&#1085;&#1086;&#1074; &#1044;&#1080;&#1085;&#1080;&#1103;&#1088; &#1056;&#1077;&#1085;&#1072;&#1090;&#1086;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>6</TD></TR>
<TR><TD>&#1048;&#1075;&#1085;&#1072;&#1096;&#1077;&#1074;&#1080;&#1095; &#1057;&#1077;&#1088;&#1075;&#1077;&#1081; &#1053;&#1080;&#1082;&#1086;&#1083;&#1072;&#1077;&#1074;&#1080;&#1095;</TD><TD>72</TD><TD>5</TD></TR>
<TR><TD>&#1057;&#1077;&#1084;&#1072;&#1082; &#1057;&#1077;&#1088;&#1075;&#1077;&#1081; &#1041;&#1086;&#1075;&#1076;&#1072;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>65</TD><TD>4</TD></TR>
<TR><TD>&#1057;&#1077;&#1084;&#1096;&#1086;&#1074; &#1048;&#1075;&#1086;&#1088;&#1100; &#1055;&#1077;&#1090;&#1088;&#1086;&#1074;&#1080;&#1095;</TD><TD>59</TD><TD>3</TD></TR>
<TR><TD>&#1058;&#1086;&#1088;&#1073;&#1080;&#1085;&#1089;&#1082;&#1080;&#1081; &#1044;&#1084;&#1080;&#1090;&#1088;&#1080;&#1081; &#1045;&#1074;&#1075;&#1077;&#1085;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>29</TD><TD>2</TD></TR>
<TR><TD>&#1040;&#1085;&#1102;&#1082;&#1086;&#1074; &#1040;&#1083;&#1077;&#1082;&#1089;&#1072;&#1085;&#1076;&#1088; &#1043;&#1077;&#1085;&#1085;&#1072;&#1076;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>63</TD><TD>1</TD></TR>
<TR><TD>&#1046;&#1080;&#1088;&#1082;&#1086;&#1074; &#1070;&#1088;&#1080;&#1081; &#1042;&#1072;&#1083;&#1077;&#1085;&#1090;&#1080;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>0</TD></TR>
<TR><TD>&#1040;&#1082;&#1080;&#1085;&#1092;&#1077;&#1077;&#1074; &#1048;&#1075;&#1086;&#1088;&#1100; &#1042;&#1083;&#1072;&#1076;&#1080;&#1084;&#1080;&#1088;&#1086;&#1074;&#1080;&#1095;</TD><TD>51</TD><TD>0</TD></TR>
<TR><TD>&#1050;&#1086;&#1083;&#1086;&#1076;&#1080;&#1085; &#1044;&#1077;&#1085;&#1080;&#1089; &#1040;&#1083;&#1077;&#1082;&#1089;&#1077;&#1077;&#1074;&#1080;&#1095;</TD><TD>24</TD><TD>0</TD></TR>
</TABLE>

Вместо имен столбцов во фразе ORDER BY можно использовать порядковые номера, указывающие положение в таблице столбца, по которому следует выполнить упорядочение.

Следующим запросом мы сортируем футболистов по количеству проведенных матчей. Если количество сыгранных матчей одинаково, происходит сортировка по количеству забитых мячей.

<br/>

    SELECT name AS "ФИО", matches AS "Матчи", goals "Голы"
    FROM russian_team
    ORDER BY 2 DESC, 3 DESC;

<br/>

<TABLE BORDER="1">
<TR><TH>&#1060;&#1048;&#1054;</TH><TH>&#1052;&#1072;&#1090;&#1095;&#1080;</TH><TH>&#1043;&#1086;&#1083;&#1099;</TH></TR>
<TR><TD>&#1048;&#1075;&#1085;&#1072;&#1096;&#1077;&#1074;&#1080;&#1095; &#1057;&#1077;&#1088;&#1075;&#1077;&#1081; &#1053;&#1080;&#1082;&#1086;&#1083;&#1072;&#1077;&#1074;&#1080;&#1095;</TD><TD>72</TD><TD>5</TD></TR>
<TR><TD>&#1040;&#1088;&#1096;&#1072;&#1074;&#1080;&#1085; &#1040;&#1085;&#1076;&#1088;&#1077;&#1081; &#1057;&#1077;&#1088;&#1075;&#1077;&#1077;&#1074;&#1080;&#1095;</TD><TD>68</TD><TD>16</TD></TR>
<TR><TD>&#1057;&#1077;&#1084;&#1072;&#1082; &#1057;&#1077;&#1088;&#1075;&#1077;&#1081; &#1041;&#1086;&#1075;&#1076;&#1072;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>65</TD><TD>4</TD></TR>
<TR><TD>&#1040;&#1085;&#1102;&#1082;&#1086;&#1074; &#1040;&#1083;&#1077;&#1082;&#1089;&#1072;&#1085;&#1076;&#1088; &#1043;&#1077;&#1085;&#1085;&#1072;&#1076;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>63</TD><TD>1</TD></TR>
<TR><TD>&#1057;&#1077;&#1084;&#1096;&#1086;&#1074; &#1048;&#1075;&#1086;&#1088;&#1100; &#1055;&#1077;&#1090;&#1088;&#1086;&#1074;&#1080;&#1095;</TD><TD>59</TD><TD>3</TD></TR>
<TR><TD>&#1040;&#1082;&#1080;&#1085;&#1092;&#1077;&#1077;&#1074; &#1048;&#1075;&#1086;&#1088;&#1100; &#1042;&#1083;&#1072;&#1076;&#1080;&#1084;&#1080;&#1088;&#1086;&#1074;&#1080;&#1095;</TD><TD>51</TD><TD>0</TD></TR>
<TR><TD>&#1055;&#1072;&#1074;&#1083;&#1102;&#1095;&#1077;&#1085;&#1082;&#1086; &#1056;&#1086;&#1084;&#1072;&#1085; &#1040;&#1085;&#1072;&#1090;&#1086;&#1083;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>20</TD></TR>
<TR><TD>&#1041;&#1080;&#1083;&#1103;&#1083;&#1077;&#1090;&#1076;&#1080;&#1085;&#1086;&#1074; &#1044;&#1080;&#1085;&#1080;&#1103;&#1088; &#1056;&#1077;&#1085;&#1072;&#1090;&#1086;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>6</TD></TR>
<TR><TD>&#1046;&#1080;&#1088;&#1082;&#1086;&#1074; &#1070;&#1088;&#1080;&#1081; &#1042;&#1072;&#1083;&#1077;&#1085;&#1090;&#1080;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>48</TD><TD>0</TD></TR>
<TR><TD>&#1057;&#1099;&#1095;&#1077;&#1074; &#1044;&#1084;&#1080;&#1090;&#1088;&#1080;&#1081; &#1045;&#1074;&#1075;&#1077;&#1085;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>47</TD><TD>14</TD></TR>
<TR><TD>&#1047;&#1099;&#1088;&#1103;&#1085;&#1086;&#1074; &#1050;&#1086;&#1085;&#1089;&#1090;&#1072;&#1085;&#1090;&#1080;&#1085; &#1043;&#1077;&#1086;&#1088;&#1075;&#1080;&#1077;&#1074;&#1080;&#1095;</TD><TD>47</TD><TD>7</TD></TR>
<TR><TD>&#1058;&#1086;&#1088;&#1073;&#1080;&#1085;&#1089;&#1082;&#1080;&#1081; &#1044;&#1084;&#1080;&#1090;&#1088;&#1080;&#1081; &#1045;&#1074;&#1075;&#1077;&#1085;&#1100;&#1077;&#1074;&#1080;&#1095;</TD><TD>29</TD><TD>2</TD></TR>
<TR><TD>&#1050;&#1086;&#1083;&#1086;&#1076;&#1080;&#1085; &#1044;&#1077;&#1085;&#1080;&#1089; &#1040;&#1083;&#1077;&#1082;&#1089;&#1077;&#1077;&#1074;&#1080;&#1095;</TD><TD>24</TD><TD>0</TD></TR>
<TR><TD>&#1057;&#1072;&#1077;&#1085;&#1082;&#1086; &#1048;&#1074;&#1072;&#1085; &#1048;&#1074;&#1072;&#1085;&#1086;&#1074;&#1080;&#1095;</TD><TD>13</TD><TD>9</TD></TR>
</TABLE>
