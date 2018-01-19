---
layout: page
title: Хранимые Процедуры (STORED PROCEDURES)
permalink: /plsql/stored-functions/
---

### Хранимые функции (STORED FUNCTIONS)


<br/>

### Прототип хранимой функции


    CREATE [OR REPLACE] FUNCTION function_name
    [( parameter1     [IN][OUT] [NOCOPY] sql_datatype | plsql_datatype
    [, parameter2     [IN][OUT] [NOCOPY] sql_datatype | plsql_datatype
    [, parameter(n+1) [IN][OUT] [NOCOPY] sql_datatype | plsql_datatype )]]]
    RETURN [ sql_data_type | plsql_data_type ]
    [ AUTHID [ DEFINER | CURRENT_USER ]]
    [ DETERMINISTIC | PARALLEL_ENABLED ]
    [ PIPELINED ]
    [ RESULT_CACHE [ RELIES ON table_name ]] IS
      declaration_statements
    BEGIN
      execution_statements
      RETURN variable;
    [EXCEPTION]
      exception_handling_statements
    END [function_name];
    /



Функция подобна процедуре за тем лишь исключением, что функция должна возвращать значение в ту точку, в которой она вызывается.

<br>

### Создание функции


Для создания функции используется оператор CREATE FUNCTION. Упрощенный синтаксис синтаксис имеет следующий вид:


    CREATE [OR REPLACE] FUNCTION function_name
    [(parameter [IN | OUT | IN OUT] тип [, …])]
    RETURN type
    IS | AS
    BEGIN
     execution_statements
    RETURN variable;

    END function_name;


<ul>
<li>
DETERMINISTIC - подсказка оптимизатору, позволяющая системе использовать сохраненную копию возвращенного функцией результата (при его наличии). Оптимизатор запроса определяет, следует ли выбрать сохраненную копию или же вызвать функцию повторно.
</li>
<li>
PARALLEL_ENABE - подсказка оптимизатору, решающая параллельное выполнение функции при вызове из оператора SELECT.
</li>
<li>
PIPELINED - указывает, что результаты табличной функции должны возвращаться построчно с помощью команды PIPE ROW.
</li>
</ul>

<br/>

### Получение информации о функции

    SELECT ojbect_name, aggregate, parallel
    FROM user_procedures
    WHERE objectt_name IN ('function1' , 'function2');
