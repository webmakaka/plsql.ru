---
layout: page
title: Основы языка PL/SQL
description: Основы языка PL/SQL
keywords: Основы языка PL/SQL
permalink: /plsql/plsql_basics/
---

# Основы языка PL/SQL

<p>Каждый язык имеет определенный синтаксис, лексикон и набор символов. Чтобы общаться на этом языке, необходимо изучить правила его использования. </p>

<p>Все программы на языке PL/SQL состоят из блоков.</p>

<br/><br/>

### Блок PL/SQL состоит из трех секций.

<br/><br/>

<div align="center"><img src="/img/intro/plsql-basics/plsql_blok_01.png" border="0" alt="PL/SQL BLOCK"></div>

<br/><br/>

<ul>

<li>Декларативная (необязательная) – Начинается с ключевого слова DECLARE и заканчивается там, где начинается исполняемая секция. Содержит все переменные, константы, курсоры и исключения.</li>
<li>Исполняемая (обязательная) – Начинается с ключевого слова BEGIN и заканчивается ключевым словом END. После END ставится точка с запятой. Содержит команды SQL для выборки данных из БД и команды PL/SQL для манипулирования данными в блоке.</li>
<li>Обработка исключений (необязательная) – Начинается с ключевого слова EXCEPTION. Определяет действия, которые должны выполняться при возникновении ошибок.</li>

</ul>

<br/>
<h3>Типы блоков</h3>

Программа на PL/SQL содержит один из несколько блоков. Эти блоки могут быть полностью автономными или вложенными.

<strong>Существует три типа блоков:</strong>

<ul>
<li>Анонимные блоки  (anonymous blocks);</li>
<li>Процедуры</li>
<li>Функции</li>
</ul>

<br/><br/>

<div align="center">
<img src="/img/intro/plsql-basics/plsql_blok_02.png" border="0" alt="PL/SQL BLOCK">
</div>

<br/><br/>

<strong>Анонимные блоки</strong> – (anonymous blocks) не имеют имен. Будут полезны, где необходимость в повторном вызове кода оссутствует.

<strong>Подпрограммы (subprograms)</strong> – именованные блоки PL/SQL, хранимые в базе данных. Поскольку у подпрограмм есть имена, их можно вызывать из любой требуемой точки приложения. Объявлять их можно как процедуры или функции. Обычно процерура используется для выполнения действия функция для вычисления и возврата значений.
