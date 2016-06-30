---
layout: page
title: Практика
permalink: /docs/practice/spec/sql/env/
---

    Практическое занятие I Введение

    Запустите ролик «Oracle SQL Developer Demo: Создание соединения с базой данных» и следуйте указаниям ролика
    1.	practice\labs\labs\mod02_cp_newdbconn.htm
    Запуск Oracle SQL Developer
    2. Запустите Oracle SQL Developer используя  ярлык “sqldeveloper” на рабочем столе.  
    Примечание: При первом старте SQL Developer может понадобится указать путь к java.exe file.

    Например:
    C:\Program Files\Java\jdk1.6.0_34\bin
    Создание в SQL Developer нового соединения с базой данных
    3. Создайте новое соединение с базой данных, используя следующую информацию:
    	a. Connection Name(имя соединения):  придумайте произвольное, понятное Вам название соединения, например «HR – demo.virtual.box» или «myconnection»
    	b. Username(пользователь): hr
    	c. Password(пароль): hr (или сообщит инструктор)
    	d. Hostname(хост): Имя или IP адрес компьютера, на котором находится учебная база данных: demo.virtual.box (или сообщит инструктор)
    	e. Port: 1521 (сообщит инструктор)
    f. Service Name: demo.virtual.box (сообщит инструктор)
    g. Включите флажок «Save Password».

    Практическое занятие I Введение (продолжение)
    Тест и соединение с базой данных
    4. Для создания нового соединения в «Connections Navigator» на узле Connections щелкните правой кнопкой. Выберите из появившегося меню «New Connection». Появится диалог «New/Select Database Connection».
    5. Протестируйте созданное соединение.
    6. Если тест прошел успешно , соединитесь с базой данных нажав кнопку «Connect».

    Просмотр таблиц в Навигаторе
    7. В «Connections Navigator» посмотрите список объектов узла «Tables». Убедитесь в том, что присутствуют следующие таблицы:
    COUNTRIES, DEPARTMENTS, EMPLOYEES, JOB_GRADES, JOB_HISTORY,
    JOBS, LOCATIONS, REGIONS
    8. Покажите структуру таблицы  EMPLOYEES.
    9. Просмотрите содержимое таблицы DEPARTMENTS.
    Откройте окно «SQL Worksheet»
    10. Откройте новый «SQL Worksheet». Изучите кнопки на панели  «SQL Worksheet». В процессе изучения «SQL Worksheet» обратите внимание на кнопки «Execute Statement» и «Run Script».
