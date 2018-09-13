---
layout: page
title: Вопросы на собеседовании на позиции PLSQL программист
permalink: /other/interview-questions/
---

# Вопросы на собеседовании на позиции PL/SQL программист:

<br/>

Лично у меня, на моем интервью по PL/SQL обычно спрашивали достаточно простые вещи. Вроде if / else и в зависимости от ветви вызвать ту или иную процедуру.<br/>

Правда нужно отметить, что я никогда не работал чисто PL/SQL программистом. Скорее так, по мелочи.

<br/>

Ниже реальный пример от коллеги, когда он куда-то ходил собеседоваться. Copy / Paste

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

<br/>

### Задание для меня на позицию Node.js разработчика

Заинтересовало ваше резюме, предварительно хотелось бы уточнить ваш уровень владения SQL, который для наших задач критичен, ответьте, пожалуйста, вот на такую задачку:

    Дано три таблицы:

    Таблица А: имена пользователей
    id | name
    -------------
    1 | Василий
    2 | Егор
    3 | Николай
    5 | Степан

    Таблица Б: отчества пользователей
    id | patronymic
    1 | Харитонович
    2 | Егорьевич
    4 | Николаевич
    5 | Тимофеевич

    Таблица В: фамилии пользователей
    id | surname
    1 | Пупкин
    2 | Егоров
    5 | Разин
    6 | Пихтин

    Напишите три SQL запроса:

    1) который выводит пользователей с полностью заполненными данными;

    2) который выводит пользователей, у которых не заполнено какое-либо поле (имя, отчество, фамилия).

    3) выводит фамилию и имя пользователя по его имени.

<br/>

**Решение:**

    -- Подготовительная часть

    CREATE TABLE user_names
    ( id number(2) NOT NULL,
      user_name varchar2(50) NOT NULL
    );


    CREATE TABLE user_middle_names
    ( id number(2) NOT NULL,
      user_middle_name varchar2(50) NOT NULL
    );

    CREATE TABLE user_last_names
    ( id number(2) NOT NULL,
      user_last_name varchar2(50) NOT NULL
    );


    INSERT INTO user_names (id, user_name) VALUES (1, 'Василий');
    INSERT INTO user_names (id, user_name) VALUES (2, 'Егор');
    INSERT INTO user_names (id, user_name) VALUES (3, 'Николай');
    INSERT INTO user_names (id, user_name) VALUES (5, 'Степан');

    select * from user_names;


    INSERT INTO user_middle_names (id, user_middle_name) VALUES (1, 'Харитонович');
    INSERT INTO user_middle_names (id, user_middle_name) VALUES (2, 'Егорьевич');
    INSERT INTO user_middle_names (id, user_middle_name) VALUES (4, 'Николаевич');
    INSERT INTO user_middle_names (id, user_middle_name) VALUES (5, 'Тимофеевич');


    select * from user_middle_names;


    INSERT INTO user_last_names (id, user_last_name) VALUES (1, 'Пупкин');
    INSERT INTO user_last_names (id, user_last_name) VALUES (2, 'Егоров');
    INSERT INTO user_last_names (id, user_last_name) VALUES (5, 'Разин');
    INSERT INTO user_last_names (id, user_last_name) VALUES (6, 'Пихтин');


    select * from user_last_names;

    ---------------------------------------------------------------------------------
    -- Задание

    -- 1) который выводит пользователей с полностью заполненными данными;

    select user_last_names.user_last_name, user_names.user_name, user_middle_names.user_middle_name
    from user_last_names, user_names, user_middle_names
    where user_last_names.id = user_names.id
    and user_last_names.id = user_middle_names.id

    -- 2) который выводит пользователей, у которых не заполнено какое-либо поле (имя, отчество, фамилия).

    select user_last_name, user_name, user_middle_name
    from (

        SELECT user_last_names.user_last_name, user_names.user_name, user_middle_names.user_middle_name
        FROM user_last_names
        FULL OUTER JOIN user_names ON user_last_names.id=user_names.id
        FULL OUTER JOIN user_middle_names ON user_last_names.id=user_middle_names.id

    )

    where
    user_last_name is null OR user_name is null  OR user_middle_name is null


    -- 3) выводит фамилию и имя пользователя по его имени.

    select user_last_name, user_name
    from (

        SELECT user_last_names.user_last_name, user_names.user_name, user_middle_names.user_middle_name
        FROM user_last_names
        FULL OUTER JOIN user_names ON user_last_names.id=user_names.id
        FULL OUTER JOIN user_middle_names ON user_last_names.id=user_middle_names.id

    )
    where user_name = 'Егор';

<br/>

<div align="center">
	<img src="//files.plsql.ru//img/interview/ph-query1.png" alt="Oracle DBA" border="0" />
</div>

<br/>

<div align="center">
	<img src="//files.plsql.ru//img/interview/ph-query2.png" alt="Oracle DBA" border="0" />
</div>

<br/>

<div align="center">
	<img src="//files.plsql.ru//img/interview/ph-query3.png" alt="Oracle DBA" border="0" />
</div>

Наверное, можно сделать лушче!

<br/>
<br/>

Есть вопросы которые следует добавить? Можно даже написать в какой компании, что спрашивали.

<div align="left">
	Обратная связь:  <br/><img src="http://img.fotografii.org/a3333333mail.gif" alt="Marley" border="0" />
</div>
