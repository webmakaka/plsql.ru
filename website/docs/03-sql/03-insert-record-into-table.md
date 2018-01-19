---
layout: page
title: Добавить запись в таблицу базы данных Oracle (INSERT)
permalink: /sql/insert-records-into-table/
---

### Добавить запись в таблицу базы данных Oracle (INSERT)



Ниже перечислены разрешенные в Oracle типы данных столбцов, с которыми приходится работать чаще других:


<ul>
<li>
NUMBER – Тип данных, используемый для хранения числовых данных. В столбцах этого типа не допускаются дефисы, текст или любая другая нечисловая информация.
</li>

<li>

DATE – Тип данных, используемый для хранения информации о датах.  Во внутреннем представлении Oracle хранит даты как числа, которые могут быть затем конвертированы в любой формат DATE по вашему желанию. По умолчанию информация в формате DATE представляется в формате DD-MON-YY (например, 25-DEC-79)/

</li>
<li>

VARCHAR2 – Этот тип данных используется для хранения текстовых данных. В столбце типа VARCHAR2 могут  храниться любые текстовые символы (включая спецсимволы, числа, буквы, дефисы и тому подобное).

</li>
<li>

CHAR – Этот тип данных используется для хранения текстовых данных. В столбце типа CHAR могут храниться любые текстовые символы (включая спецсимволы, числа, буквы, дефисы и тому подобное). В этом случае, если записанный текст имеет длину, меньшую указанной в определении переменной, он будет дополнен справа пробелами. Следовательно, фамилия SCOTT, если ее поместить в столбец, определенный как CHAR(10), будет дополнена справа пять пробелами.

</li>
</ul>


Главное различие между столбцами CHAR и VARCHAR2 состоит в том, что размер памяти, требующейся для хранения текстовых данных в столбце CHAR, всегда превышает размер памяти для хранения той же информации в столбце VARCHAR2. Это связано с тем, что столбцы CHAR имеют фиксированную длину и всегда содержат одинаковое количество байтов, в то время как столбцы VARCHAR2 имеют переменную длину и содержат ровно столько байтов, сколько вы предоставили для записи.


В Oracle существуют и типы данных для хранения других типов информации; однако их не так много, как в базах данных других производителей. Например, в Oracle отсутствует тип данных для хранения валют. Значение этого типа рассматриваются как простые числа и как таковые их можно хранить в столбцах типа NUMBER.

<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Аршавин Андрей Сергеевич',
      'Нападающий',
      10,
      68,
      16,
      'Арсенал (Лондон)',
      TO_DATE('29.05.1981','DD-MM-YYYY')
      );


<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Акинфеев Игорь Владимирович',
      'Вратарь',
      1,
      51,
      0,
      'ЦСКА (Москва)',
      TO_DATE('08.04.1986','DD-MM-YYYY')
    );


<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Анюков Александр Геннадьевич',
      'Защитник',
      22,
      63,
      1,
      'Зенит (Санкт-Петербург)',
      TO_DATE('28.09.1982','DD-MM-YYYY')
    );


<br/>

    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Игнашевич Сергей Николаевич',
      'Защитник',
      4,
      72,
      5,
      'ЦСКА (Москва)',
      TO_DATE('14.07.1979','DD-MM-YYYY')
    );



<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Колодин Денис Алексеевич',
      'Защитник',
      8,
      24,
      0,
      'Динамо (Москва)',
      TO_DATE('11.01.1982','DD-MM-YYYY')
    );


<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Саенко Иван Иванович',
      'Полузащитник',
      8,
      13,
      9,
      'Спартак (Москва)',
      TO_DATE('17.10.1983','DD-MM-YYYY')
    );


<br/>

    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Торбинский Дмитрий Евгеньевич',
      'Полузащитник',
      7,
      29,
      2,
      'Локомотив (Москва)',
      TO_DATE('28.04.1984','DD-MM-YYYY')
    );


<br/>

    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Семак Сергей Богданович',
      'Полузащитник',
      11,
      65,
      4,
      'Зенит (Санкт-Петербург)',
      TO_DATE('27.02.1976','DD-MM-YYYY')
    );



<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Зырянов Константин Георгиевич',
      'Полузащитник',
      17,
      47,
      7,
      'Зенит (Санкт-Петербург)',
      TO_DATE('05.10.1977','DD-MM-YYYY')
    );

<br/>


    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Семшов Игорь Петрович',
      'Полузащитник',
      20,
      59,
      3,
      'Динамо (Москва)',
      TO_DATE('06.04.1978','DD-MM-YYYY')
    );


<br/>

    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Билялетдинов Динияр Ренатович',
      'Полузащитник',
      15,
      48,
      6,
      'Эвертон (Ливерпуль)',
      TO_DATE('27.02.1985','DD-MM-YYYY')
    );


<br/>

    INSERT INTO russian_team
      (
      id,
      name,
      position,
      player_number,
      matches,
      goals,
      club,
      birthday
    )
    VALUES
      (
      russian_team_id_sequence.NEXTVAL,
      'Жирков Юрий Валентинович',
      'Полузащитник',
      18,
      48,
      0,
      'Анжи (Махачкала)',
      TO_DATE('20.08.1983','DD-MM-YYYY')
    );


<br/>

    INSERT INTO russian_team
        (
        id,
        name,
        position,
        player_number,
        matches,
        goals,
        club,
        birthday
      )
      VALUES
        (
        russian_team_id_sequence.NEXTVAL,
        'Павлюченко Роман Анатольевич',
        'Нападающий',
        19,
        48,
        20,
        'Тоттенхэм (Лондон)',
        TO_DATE('15.12.1981','DD-MM-YYYY')
      );


<br/>

      INSERT INTO russian_team
        (
        id,
        name,
        position,
        player_number,
        matches,
        goals,
        club,
        birthday
      )
      VALUES
        (
        russian_team_id_sequence.NEXTVAL,
        'Сычев Дмитрий Евгеньевич',
        'Нападающий',
        21,
        47,
        14,
        'Локомотив (Москва)',
        TO_DATE('26.10.1983','DD-MM-YYYY')
      );
