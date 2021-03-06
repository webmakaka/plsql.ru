---
layout: page
title: Ограничение числа сгруппированных данных (HAVING)
description: Ограничение числа сгруппированных данных (HAVING)
keywords: Ограничение числа сгруппированных данных, HAVING
permalink: /sql/having/
---

# Ограничение числа сгруппированных данных (HAVING)

```
SELECT  club AS "Клуб", COUNT(position)
FROM russian_team
GROUP BY club
ORDER BY COUNT(position) DESC;
```

<br/><br/>

<TABLE BORDER="1">
<TR><TH>&#1050;&#1083;&#1091;&#1073;</TH><TH>COUNT(POSITION)</TH></TR>
<TR><TD>&#1047;&#1077;&#1085;&#1080;&#1090; (&#1057;&#1072;&#1085;&#1082;&#1090;-&#1055;&#1077;&#1090;&#1077;&#1088;&#1073;&#1091;&#1088;&#1075;)</TD><TD>3</TD></TR>
<TR><TD>&#1044;&#1080;&#1085;&#1072;&#1084;&#1086; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>2</TD></TR>
<TR><TD>&#1051;&#1086;&#1082;&#1086;&#1084;&#1086;&#1090;&#1080;&#1074; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>2</TD></TR>
<TR><TD>&#1062;&#1057;&#1050;&#1040; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>2</TD></TR>
<TR><TD>&#1069;&#1074;&#1077;&#1088;&#1090;&#1086;&#1085; (&#1051;&#1080;&#1074;&#1077;&#1088;&#1087;&#1091;&#1083;&#1100;)</TD><TD>1</TD></TR>
<TR><TD>&#1057;&#1087;&#1072;&#1088;&#1090;&#1072;&#1082; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>1</TD></TR>
<TR><TD>&#1040;&#1088;&#1089;&#1077;&#1085;&#1072;&#1083; (&#1051;&#1086;&#1085;&#1076;&#1086;&#1085;)</TD><TD>1</TD></TR>
<TR><TD>&#1058;&#1086;&#1090;&#1090;&#1077;&#1085;&#1093;&#1101;&#1084; (&#1051;&#1086;&#1085;&#1076;&#1086;&#1085;)</TD><TD>1</TD></TR>
<TR><TD>&#1040;&#1085;&#1078;&#1080; (&#1052;&#1072;&#1093;&#1072;&#1095;&#1082;&#1072;&#1083;&#1072;)</TD><TD>1</TD></TR>
</TABLE>

<br/><br/>
После того, как данные сгруппированы с помощью фразы GROUP BY, иногда бывает полезно отфильтровать нежелательные данные.
<br/><br/>

    SELECT  club AS "Клуб", COUNT(position)
    FROM russian_team
    GROUP BY club
    HAVING COUNT(position) >= 2
    ORDER BY COUNT(position) DESC;

<br/><br/>

<TABLE BORDER="1">
<TR><TH>&#1050;&#1083;&#1091;&#1073;</TH><TH>COUNT(POSITION)</TH></TR>
<TR><TD>&#1047;&#1077;&#1085;&#1080;&#1090; (&#1057;&#1072;&#1085;&#1082;&#1090;-&#1055;&#1077;&#1090;&#1077;&#1088;&#1073;&#1091;&#1088;&#1075;)</TD><TD>3</TD></TR>
<TR><TD>&#1062;&#1057;&#1050;&#1040; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>2</TD></TR>
<TR><TD>&#1044;&#1080;&#1085;&#1072;&#1084;&#1086; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>2</TD></TR>
<TR><TD>&#1051;&#1086;&#1082;&#1086;&#1084;&#1086;&#1090;&#1080;&#1074; (&#1052;&#1086;&#1089;&#1082;&#1074;&#1072;)</TD><TD>2</TD></TR>
</TABLE>
