---
layout: page
title: Конкатенация переменных в блоке PL/SQL для формирования запроса
permalink: /other/variables-concat/
---


# Конкатенация переменных в блоке PL/SQL для формирования запроса

<br/>

    -- L_LOGGED_IN_USER2 := 'test_user';

    SELECT SYS_CONTEXT ('SEC_CTX', 'user_id') INTO L_LOGGED_IN_USER FROM DUAL;


<br/>


    L_RES := '(select my_value ' ||
           'from my_tables ' ||
           'where any_condition ' ||  

           -- Явно задаю значение, чтобы пришло в запрос 'pertov'
           -- 'and login = ' || '''pertov''' || ')';  

           -- Переменную определенную в коде
           -- 'and login = ''' || L_LOGGED_IN_USER2 || ''')';

           -- Переменную взятую из запроса
           'and login = ''' || L_LOGGED_IN_USER || ''')';
