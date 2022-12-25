---
layout: page
title: Как задать столбцам значимые имена
description: Как задать столбцам значимые имена
keywords: Как задать столбцам значимые имена
permalink: /books/molinaro/retrieving_records/providing-meaningful-names-for-columns/
---

# Как задать столбцам значимые имена

<h3>Задача</h3>

Требуется изменить имена возвращенных в результате запроса столбцов, чтобы сделать их более понятными и удобными для чтения. Рассмотрим запрос, возвращающий зарплаты и комиссионные всех служащих.

    select e.sal, e.comm
    from emp e

<br/>

    SAL COMM
    --- ----
    800
    1600  300
    1250  500
    2975
    1250 1400
    2850
    2450
    3000
    5000
    1500    0
    1100
    950
    3000
    1300

     14 rows selected

Что такое "sal"? Сокращенная запись "sale" (продажа)? Может это чье-то имя? Что означает "comm"? Сокращение от "communications" (обобщение)? Столбы в результирующем наборе должны иметь более понятные названия.

<h3>Решение</h3>

Чтобы изменить имена в результаттах запроса, используйте ключевое слово AS следующим образом: исходное*имя AS новое*имя.
Для некоторых баз данных применение AS необязательно, но во всех оно допускается:

    select e.sal as salary, e.comm as commission
    from emp e

<br/>

    SALARY COMMISSION
    ------ ----------
       800
      1600        300
      1250        500
      2975
      1250       1400
      2850
      2450
      3000
      5000
      1500          0
      1100
       950
      3000
      1300

     14 rows selected

<h3>Обсуждение</h3>

Задавая новые имена возвращаемым запросом столбцам с помощью клшючевого слова AS, мы присваиваем псеводимы (aliasing) этим столбцам. Новые имена являются псевдонимами (aliases). Хорошо подобранные псевдонимы способствуют пониманию запроса и его результатов пользователями.

Если нужно в описание столбца указать несколько слов, воспользуйтесь двойными кавычками.

    select e.sal as "Зарплата за май", e.comm as "Комиссия за май"
    from emp e

<br/>

    Зарплата за май Комиссия за май
    --------------- ---------------
                800
               1600             300
               1250             500
               2975
               1250            1400
               2850
               2450
               3000
               5000
               1500               0
               1100
                950
               3000
               1300

     14 rows selected