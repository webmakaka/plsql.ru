---
layout: page
title: Среды программирования для языка PL/SQL
permalink: /prepare-to-development/ide_for_plsql_development/
---


# Среды программирования для языка PL/SQL


<p>Из сред разработки, можно воспользоваться бесплатным средством <a href="http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html" rel="nofollow">Oracle SQL Developer</a>. Я установил на рабочем компьютере Oracle Linux и смог отказаться от PL/SQL developer в пользу этого бесплатного средства. Впрочем, я сейчас больше выполняю запросы, чем что-то программирую на PL/SQL.

<br/><br/>

Среди платных, можно выделить:

<ul>
    <li><a href="http://www.allroundautomations.com/plsqldev.html" rel="nofollow">PL/SQL Developer</a></li>
    <li><a href="http://toadfororacle.com/index.jspa" rel="nofollow">TOAD</a></li>
    <li>SQL Navigator (мало кто пользуется)</li>
    <li><a href="http://www.sqlmaestro.com/products/oracle/maestro/" rel="nofollow">Oracle Maestro (мало кто пользуется)</a></li>
</ul>

<br />

Версии платных программ доступны для ознакомления. </p>

<br />

<p>Для подключения сред разработки к серверу баз данных, в большинстве случаев, необходимо установить на компьютер, с которого Вы будете подключаться к базе данных <a href="http://odba.ru/showthread.php?t=325">Oracle Client</a> и создать файл (tnsnames.ora) с описанием параметров подключения к серверу. Если вы устанавливаете клиент Enterprise версии, вы можете создать этот файл довольно легко с помощью "мастера подключений". </p>


<a href="http://odba.ru/showthread.php?t=325">Пример инсталляции Oracle Client в Windows</a>. Если будет что-то непонятно, пишите, попытаюсь объяснить или переделать инструкцию.

<p>SQL Developer не требует установленного Client'а.</p>