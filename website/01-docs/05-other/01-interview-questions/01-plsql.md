---
layout: page
title: Вопросы на собеседовании на позиции PL/SQL программист
description: Вопросы на собеседовании на позиции PL/SQL программист
keywords: Вопросы на собеседовании, PL/SQL программист
permalink: /other/interview-questions/plsql/
---

# Вопросы на собеседовании на позиции PL/SQL программист:

<br/>

Лично у меня, на моем интервью по PL/SQL обычно спрашивали достаточно простые вещи. Вроде if / else и в зависимости от ветви вызвать ту или иную процедуру.<br/>

Правда нужно отметить, что я никогда не работал чисто PL/SQL программистом. Скорее так, по мелочи.
Запомнился вопрос.

<br/>

### Как одной командой удалить все дубликаты из таблицы.

<br/>

```
SELECT * FROM
  employees e
WHERE
  e.rowid <>
    (
      SELECT
        MAX(ee.rowid)
      FROM
                employees ee
            WHERE
        ee.first_name = e.first_name
        AND ee.last_name = e.last_name
        AND ee.age = e.age
    );
```

https://t.me/oracle_dba_ru/9200

<br/>

```
delete FROM t_table e
WHERE
  e.rowid <>
    (
      SELECT
        MAX(ee.rowid)
      FROM t_table ee
      WHERE
          ee.date_p = e.date_p
      AND ee.product_p = e.product_p
    );
```

<br/>

https://t.me/oracle_dba_ru/9212

<br/>

См. также:  
https://www.sql.ru/faq/faq_topic.aspx?fid=711

<br/>

**Ниже реальный пример от коллеги, когда он куда-то ходил собеседоваться. Copy / Paste**

<br/>

```plsql
-- Что делает эта функция?
function ХХХХХ(date_from date, date_to date) return number as
    n number;
  begin
    if (date_from is null) or (date_to is null) then
      return 0;
    else
      begin
        select count(*)
          into n
          from (select rownum rnum
                  from all_objects
                  where rownum <= to_date(date_to) - to_date(date_from) + 1)
          where to_char(to_date(date_from) + rnum - 1, 'DY') not in
                ('СБ', 'ВС', 'SUN', 'SAT');
        return n;
      end;
    end if;
  end;
```
