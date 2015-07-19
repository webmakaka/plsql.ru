---
layout: page
title: Простейшая программа на PL/SQL "Hello World"
permalink: /docs/plsql/hello-world-plsql/
---

### Простейшая программа на PL/SQL: "Hello World"



Традиционно, простейшая программа, просто выводит какое-нибудь приветственное сообщение. Обычно "Hello World".<br />


Программа просто выводит текст. Для этого используется встроенная процедура put_line() из пакета DBMS_OUTPUT.<br />
Блоки BEGIN и END являются обязательными.

<br/>
<h3>Простейшая программа в командной строке</h3>


Команда SET SERVEROUTPUT ON - необходима для вывода сообщения в консоли.


    sqlplus SCOTT/TIGER
    SET SERVEROUTPUT ON
    BEGIN
    DBMS_OUTPUT.PUT_LINE('Ура Заработало');
    END;
    /


<br/>
<br/>

<div align = "center">
<img src="putty5.png" border="0" alt="plsql hello world console sample">
</div>


<br/>
<h3>Простейшая программа в профессиональной среде для разработки PL/SQL Developer</h3>


<p><img src="plsql_program_01.PNG" alt="Hello World on PL/SQL" /></p>


<br/><br />


Для выполнения написанного программного кода, нужно нажать кнопку F8. И если программа написана правильно, в нижней части экрана появится сообщение Done.

Посмотреть результат, Вы можете перейдя на вкладку Output.


<br/><br />


<p><img src="plsql_program_02.PNG" alt="Hello World on PL/SQL" /></p>
