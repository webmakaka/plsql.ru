---
layout: page
title: Демонстрационные Схемы SCOTT/TIGER и HR/HR
permalink: /docs/prepare-to-development/oracle-sample-schemas/
---


### Демонстрационные Схемы: SCOTT/TIGER и HR/HR


<p>Для изучения своих технологий, Oracle предлагает набор подготовленных схем (таблиц). Для демонстрации примеров, преимущественно используют схемы <a href="http://odba.ru/showthread.php?t=298">SCOTT/TIGER и HR/HR</a>. В данном случае SCOTT - логин пользователя, а TIGER - пароль. (Брюс Скотт – теперь уже бывший сотрудник Oracle, а Тигром звали кота его дочери).</p>


<br/>
<h3>Импорт схемы scott/tiger</h3>

Нужно отметить, что Oracle 11 чувствительна к регистру набранных символов.
<br/>
Для создания / пересоздания схемы (пользователя)  scott/tiger, подключитесь к серверу под учетной записью с правами DBA ( в случае инсталляции по инструкции приведенной выше, это учетная запись oracle11).
<br/><br/>
Выполните вход с правами суперпользователя:<br/>

    $ sqlplus / as sysdba


Выполните команду:

    @$ORACLE_HOME/rdbms/admin/utlsampl.sql


Произошел выход из интерпретатора команд SQL. Появилось сообщение следующего содержания:


    Disconnected from Oracle Database 11g Enterprise Edition Release 11.2.0.3.0 - 64bit Production
    With the Partitioning, OLAP, Data Mining and Real Application Testing options


Подключитесь к базе с использованием созданной схемы:

    $ sqlplus scott/tiger


Чтобы посмотреть какие таблицы были созданы, введите следующую команду:

    SQL> select table_name from user_tables;

<br/>

    TABLE_NAME
    ------------------------------
    SALGRADE
    BONUS
    EMP
    DEPT


Для выхода из интерпретатора команд SQL.<br/>

    SQL> quit

<br/>
<h3>Импорт схемы HR/HR</h3>

<strong> Схема HR/HR достаточно большая Поэтому мы сохранили ее в виде файла.
Для создания этой схемы выполните следующие команды: </strong>



    $ cd /tmp

<br/>

    $ wget http://plsql.ru/website/docs/02-prepare-to-development/04-oracle-sample-schemas/hr.sql

<br/>

    $ sqlplus / as sysdba

<br/>

    SQL> @hr.sql


Посмотрите результаты выполнения скрипта и убедитесь, что имеющиеся ошибки (если они конечно есть) несущественны, для работы с данной схемой.


    $ less hr.lst
