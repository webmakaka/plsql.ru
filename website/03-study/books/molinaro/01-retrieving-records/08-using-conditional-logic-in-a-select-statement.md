---
layout: page
title: Использование условной логики в выражении SELECT
permalink: /books/molinaro/retrieving_records/using-conditional-logic-in-a-select-statements/
---

### Использование условной логики в выражении SELECT


<h3>Задача</h3>

Требуется осуществить операцию IF-ELSE в выражении SELECT. Например, необходимо сформировать результирующее множество, в котором для служащих, получающих $2000 или менее, возвращается значение "UNDERPAID" (низкооплачиваемый), для служащих, получающих $4000 или более, возвращается значение "OVERPAID" (высокооплачиваемый), и для служащи, заработная плата которых находится между $2000 и $4000, возвращается значение "OK".



<h3>Решение</h3>

Для осуществления услввной логики непосредственно в выражении SELECT используйте выражение CASE:


    select e.ename, e.sal,
        case when e.sal <= 2000 then 'UNDERPAID'
             when e.sal >= 4000 then 'OVERPAID'
             else 'OK'
        end as status
    from emp e


<br/>

    ENAME      SAL STATUS  
    ---------- --- ---------
    SMITH      800 UNDERPAID
    ALLEN      1600 UNDERPAID
    WARD       1250 UNDERPAID
    JONES      2975 OK
    MARTIN     1250 UNDERPAID
    BLAKE      2850 OK
    CLARK      2450 OK
    SCOTT      3000 OK
    KING       5000 OVERPAID  
    TURNER     1500 UNDERPAID
    ADAMS      1100 UNDERPAID
    JAMES      950 UNDERPAID
    FORD       3000 OK
    MILLER     1300 UNDERPAID

     14 rows selected  



<h3>Обсуждение</h3>


Выражение CASE позволяет применять условную логику к возвращаемым в результате запроса значениям. В целях формирования более удобного для чтения результирующего множества, можно указать псевдоним для выражения CASE. В данном решении результаты выразения CASE выводятся в столбце под псевдонимом STATUS. Конструкция ELSE является необязательной. Если ELSE опущено, выражение CASE возвратит NULL для любой не удовлетворяющей условию строки.
