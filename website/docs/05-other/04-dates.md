---
layout: page
title: Примеры работы с датами в Oracle
permalink: /docs/other/dates/
---

    -- Текущий день недели
    select trunc (SYSDATE) from dual;

<br/>

    -- Вчера
    select trunc (SYSDATE-1) from dual;

<br/>
<strong>Текущая неделя</strong>

    -- Первый день недели
    select trunc(SYSDATE, 'DAY') from dual;
    -- Output: 30.05.2016

<br/>

    -- Последний день недели
    select trunc(SYSDATE, 'DAY')+6 from dual;
    -- Output: 05.06.2016

<br/>
<strong>Прошедшая неделя</strong>

    -- Первый день прошедшей недели
    select trunc(SYSDATE, 'DAY') -7 from dual;
    -- Output: 23.05.2016

<br/>

    -- Последний день прошедшей недели
    select trunc(SYSDATE, 'DAY')-1 from dual;
    -- Output: 29.05.2016

<br/>
<strong>Следующая неделя</strong>

    -- Первый день следующей недели
    select trunc(SYSDATE, 'DAY') +7 from dual;
    -- Output: 06.06.2016

<br/>

    -- Последний день следующей недели
    select trunc(SYSDATE, 'DAY') +13 from dual;
    -- Output: 12.06.2016

<br/>

<strong>Текущий месяц</strong>

    -- Первый день месяца
    select trunc (SYSDATE, 'MM') from dual;

<br/>

    -- Последний день месяца
    select trunc (last_day(sysdate)) from dual;

<br/>

<strong>Прошедший месяц</strong>

    -- Первый день прошлого месяца
    select trunc(ADD_MONTHS(SYSDATE, -1), 'MM') from dual;

<br/>

    -- Последний день прошлого месяца
    select trunc (SYSDATE, 'MM') -1 from dual;

<br/>

<strong>Следующий месяц</strong>

    -- Первый день следующего месяца
    select trunc (last_day(sysdate)) +1 from dual;

<br/>

    -- Последний день следующего месяца
    select trunc(LAST_DAY(ADD_MONTHS(SYSDATE, 1))) from dual;

<br/>
<strong>Текущий квартал</strong>

    -- Первый день квартала
    select trunc (SYSDATE, 'Q') from dual;

    -- Последний день квартала
    select add_months(trunc(sysdate,'q'),3)-1 from dual;


<br/>
<strong>Прошлый квартал</strong>

    -- Первый день прошлого квартала
    select trunc(add_months(sysdate,-3),'q') from dual;

    -- Последний день прошлого квартала
    select add_months(trunc(add_months(sysdate,-3),'q'),3)-1 from dual;


<br/>
<strong>Следующий квартал</strong>

    -- Первый день следующего квартала
    select add_months(trunc(sysdate,'q'),3) from dual;

    -- Последний день следующего квартала
    select add_months(trunc(add_months(sysdate,3),'q'),3)-1 from dual;


<br/>
<strong>Текущий год</strong>

    -- Первый день года
    select trunc (SYSDATE, 'Y') from dual;

    -- Последний день года
    select ADD_MONTHS(trunc (SYSDATE, 'YEAR'),12)-1 FROM DUAL;

<br/>
<strong>Прошедший год</strong>

    -- Первый день прошлого года
    select ADD_MONTHS (trunc (SYSDATE, 'YEAR'), -12) FROM DUAL;


    -- Последний день прошлого года
    select ADD_MONTHS (trunc (SYSDATE, 'YEAR'), -1 ) +30 FROM DUAL;


Нужно будет упростить вычисления, если это возможно.  
Я писал на лету и сам эти вычисления не использую. Т.е. допускаю, что где-то закрлась ошибка. Если что, поправлю.
