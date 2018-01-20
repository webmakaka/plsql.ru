---
layout: page
title: Циклы (LOOPS)
permalink: /plsql/loops/
---

# Циклы (LOOPS)


Циклы используются для того, чтобы можно было несколько раз выполнить один или несколько операторов. В PL/SQL есть три типа циклов:

<ul>
<li>Простые циклы  - выполняются до тех пор, пока цикл явно не закончится.</li>
<li>Циклы WHILE - выполняются до тех пор, пока не произойдет определенное условие.</li>
<li>Циклы FOR - выполняются предварительно заданное число раз.</li>
</ul>


<br/>

### Прототип цикла  FOR

    FOR i IN starting_number..ending_number LOOP
      statement;
    END LOOP;



<br/>

    FOR i IN {cursor_name[(parameter1,parameter(n+1))] | (sql_statement)} LOOP
      statement;
    END LOOP;


<br/>

    FOR range_index IN range_bottom..range_top LOOP
      repeating_statements;
    END LOOP;


<br/>

### Прототип цикла WHILE


    WHILE entry_condition LOOP
     [counter_management_statements;]
      repeating_statements;
    END LOOP;
