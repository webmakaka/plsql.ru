---
layout: page
title: Хранимые Процедуры (STORED PROCEDURES)
permalink: /plsql/stored-procedures/
---

# Хранимые Процедуры (STORED PROCEDURES)


<br/>

### Прототип хранимой процедуры


    CREATE [OR REPLACE]  PROCEDURE procedure_name
    [( parameter1     [IN][OUT] [NOCOPY] sql_datatype | plsql_datatype
    [, parameter2     [IN][OUT] [NOCOPY] sql_datatype | plsql_datatype
    [, parameter(n+1) [IN][OUT] [NOCOPY] sql_datatype | plsql_datatype )]]]
    [ AUTHID DEFINER | CURRENT_USER ] IS
      declaration_statements
    BEGIN
      execution_statements
    [EXCEPTION]
      exception_handling_statements
    END [procedure_name];
    /



<br/>

### Создание процедуры


Для создания процедуры используется оператор CREATE PROCEDURE.


Упрощенный синтаксис оператора CREATE PROCEDURE выглядит следующим образом.


    CREATE [OR REPLACE] PROCEDURE procedure_name
    [(имя_параметра [IN | OUT | IN OUT] тип [, …])]
    IS | AS
    BEGIN
    тело процедуры
    END имя_процедуры


OR REPLACE – если процедура с таким же именем уже хранится в базе данных, то с данным параметром, она просто заменит существующую. Без этого параметра, если процедура с данным именем уже существует, появится сообщение об ошибке.


IN \| OUT \| IN OUT – специфицирует режим параметров. Для каждого параметра можно выбрать один из следующих режимов:



<ul>
<li>
IN – режим по умолчанию для параметра. К моменту выполнения параметр должен иметь значение и это значение не изменится в результате выполнения процедуры.
</li>
<li>
OUT – специфицируется для параметров,  значения которых устанавливаются только в теле процедуры.
</li>
<li>
IN OUT - специфицируется для параметров, которые могу иметь значение к моменту вызова процедуры, но эти значения могут быть изменены в теле процедуры.
</li>
<li>
AUTHID  - определяет, с какими правами будет исполняться процедура: с правами ее владельца (создателя) или же с правами вызывающего пользователя.
</li>
</ul>



<br/>

### Вызов процедуры


Для вызова процедуры испоьзуется оператор CALL

    CALL  procedure_name ([( parameter1 , [parameter(n+1)]]);



<br/>

### Получение информации о процедурах


Получить информацию о процедурах можно из представления user_procedures.

Информацию обо всех процедурах, которым вы имеете доступ, можно получить из представления all_procedures

    SELECT ojbect_name, aggregate, parallel
    FROM user_procedures
    WHERE objectt_name='procedure_name';




<br/>

### Удаление процедуры


    DROP PROCEDURE procedure_name;

<br/>

### Просмотр ошибок в процедуре

Если во время создания процедуры база данных сообщает об ошбике, можно увидеть эти ошибки, задав команду SWHOW ERRORS.
