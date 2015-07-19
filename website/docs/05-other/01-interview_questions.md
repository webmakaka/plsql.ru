---
layout: page
title: Вопросы на собеседовании
permalink: /docs/other/interview_questions/
---

### Вопросы на собеседовании:


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

<br/>


Есть вопросы которые следует добавить?

<div align="left">
	Обратная связь:  <br/><img src="http://img.fotografii.org/a3333333mail.gif" alt="Marley" border="0" />
</div>
