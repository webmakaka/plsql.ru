---
layout: page
title: Таблицы (TABLES)
permalink: /sql/create_table/
---

# Таблицы (TABLES):

Базы данных - представляют из себя (главным образом) большое количество таблиц. Почти таких-же как изображенная на рисунке. В отличие от обычных таблиц, с таблицами в базах данных могут одновременно работать большое количество людей.

<br/><br/>

<div align="center">
<img src="//files.plsql.ru/sql/create-table/table.png" border="0" alt="Tables">
</div>

<br/><br/>

Перед тем как создать таблицу в базе данных Oracle, возможно, имеет смысл взять листок бумаги и карандаш и попробовать нарисовать таблицу. Далее, следует одну-две строки заполнить данными.


В каждом из столбцов должны храниться данные одного типа. Вы определяете будет ли это число, текст, дата или это будут данные какого-либо другого типа. Помимо этого, вы определяете, если это текст, какова его максимально возможная длина. Если число, будет ли у него дробная часть, если дата, в каком формате она будет представлена.


<br/>
<h3>Создание пользователя, который будет создавать таблицы</h3>


Необходимо подключиться к базе под учетной записью пользователя с административными правами (например, system)и создать пользователя который сможет создавать, удалять и вносить изменения в таблицы.

<br/><br/>

<div align="center">
<img src="//files.plsql.ru/sql/create-table/system.png" border="0" alt="system as sysem">
</div>

<br/><br/>

<div align="center">
<img src="//files.plsql.ru/sql/create-table/create-user.png" border="0" alt="creating user manager">
</div>

<br/><br/>


    CREATE USER manager
    IDENTIFIED BY manager
    TEMPORARY TABLESPACE MY_TEMP
    DEFAULT TABLESPACE MY_DATA;


<br/>

    GRANT CONNECT TO manager;
    GRANT RESOURCE TO manager;


<br/>
<h3>Создание таблицы в базе данных Oracle</h3>


<div align="center">
<img src="//files.plsql.ru/sql/create-table/manager-as-manager.png" border="0" alt="manager as manager">
</div>

<br/><br/>

Не нашел ничего лучшего, чтобы создать таблицу, в которую решил поместить информацию о футболистах сборной России по футболу.
<br/><br/>

Для того, чтобы каждый раз при добавлении новой записи в таблицу базы данных Oracle, идентификатор строки автоматически увеличивался (Автоинкремент) приходится использовать последовательности (SEQUENCE).

<br/><br/>


    CREATE SEQUENCE russian_team_id_sequence
    START WITH 1
    INCREMENT BY 1;

<br/>

    CREATE TABLE russian_team (
        id NUMBER(5) PRIMARY KEY,
        name VARCHAR2(140),
        position VARCHAR2(140),
        player_number NUMBER(2),
        matches NUMBER(3),
        goals NUMBER(3),
        club VARCHAR2(140),
        birthday DATE
    )
