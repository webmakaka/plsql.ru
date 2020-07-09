---
layout: page
title: Подготовка окружения
description: Подготовка окружения
keywords: Подготовка окружения
permalink: /books/molinaro/prepare-environment/
---

# Подготовка окружения

Используется oracle12 release 1 (последняя версия базы данных oracle на момент написания).

Необходимо подключиться к базе под учетной записью пользователя с административными правами (например, system) и создать пользователя который сможет создавать, удалять и вносить изменения в таблицы.

    -- создать пользователя manager с паролем manager
    CREATE USER manager
    IDENTIFIED BY manager;

<br/>

    -- выдать пользователю manager минимальный набор прав для подключения к базе данных и работы с объектами
    GRANT CONNECT TO manager;
    GRANT RESOURCE TO manager;

    -- выделить пользователю manager 10 мегабайт в табличном пространстве users
    ALTER USER manager QUOTA 10M ON users;

    -- предоставить пользователю manager возможность создавать представления
    -- GRANT CREATE VIEW TO manager;

<br/>

### Подключаемся созданным пользователем manager/manager и создаем таблицы для примеров.

    -- создать таблицу EMP
    CREATE TABLE EMP  (
     EMPNO NUMBER ,
     ENAME VARCHAR2(10) ,
     JOB VARCHAR2(10) ,
     MGR NUMBER ,
     HIREDATE DATE ,
     SAL NUMBER ,
     COMM NUMBER ,
     DEPTNO NUMBER
     );

<br/>

    -- Вставить в таблицу EMP данные
    INSERT INTO EMP VALUES
            (7369, 'SMITH',  'CLERK',     7902,
            TO_DATE('1980-12-17', 'yyyy-mm-dd'),  800, NULL, 20);
    INSERT INTO EMP VALUES
            (7499, 'ALLEN',  'SALESMAN',  7698,
            TO_DATE('1981-2-20', 'yyyy-mm-dd'), 1600,  300, 30);
    INSERT INTO EMP VALUES
            (7521, 'WARD',   'SALESMAN',  7698,
            TO_DATE('1981-2-22', 'yyyy-mm-dd'), 1250,  500, 30);
    INSERT INTO EMP VALUES
            (7566, 'JONES',  'MANAGER',   7839,
            TO_DATE('1981-4-2', 'yyyy-mm-dd'),  2975, NULL, 20);
    INSERT INTO EMP VALUES
            (7654, 'MARTIN', 'SALESMAN',  7698,
            TO_DATE('1981-9-28', 'yyyy-mm-dd'), 1250, 1400, 30);
    INSERT INTO EMP VALUES
            (7698, 'BLAKE',  'MANAGER',   7839,
            TO_DATE('1981-5-1', 'yyyy-mm-dd'),  2850, NULL, 30);
    INSERT INTO EMP VALUES
            (7782, 'CLARK',  'MANAGER',   7839,
            TO_DATE('1981-6-9', 'yyyy-mm-dd'),  2450, NULL, 10);
    INSERT INTO EMP VALUES
            (7788, 'SCOTT',  'ANALYST',   7566,
            TO_DATE('1982-12-9', 'yyyy-mm-dd'), 3000, NULL, 20);
    INSERT INTO EMP VALUES
            (7839, 'KING',   'PRESIDENT', NULL,
            TO_DATE('1981-11-17', 'yyyy-mm-dd'), 5000, NULL, 10);
    INSERT INTO EMP VALUES
            (7844, 'TURNER', 'SALESMAN',  7698,
            TO_DATE('1981-9-8', 'yyyy-mm-dd'),  1500,    0, 30);
    INSERT INTO EMP VALUES
            (7876, 'ADAMS',  'CLERK',     7788,
            TO_DATE('1983-1-12', 'yyyy-mm-dd'), 1100, NULL, 20);
    INSERT INTO EMP VALUES
            (7900, 'JAMES',  'CLERK',     7698,
            TO_DATE('1981-12-3', 'yyyy-mm-dd'),   950, NULL, 30);
    INSERT INTO EMP VALUES
            (7902, 'FORD',   'ANALYST',   7566,
            TO_DATE('1981-12-3', 'yyyy-mm-dd'),  3000, NULL, 20);
    INSERT INTO EMP VALUES
            (7934, 'MILLER', 'CLERK',     7782,
            TO_DATE('1982-1-23', 'yyyy-mm-dd'), 1300, NULL, 10);

<br/>

    CREATE TABLE DEPT
           (DEPTNO NUMBER,
            DNAME VARCHAR2(14),
            LOC VARCHAR2(13) );

<br/>

    INSERT INTO DEPT VALUES (10, 'ACCOUNTING', 'NEW YORK');
    INSERT INTO DEPT VALUES (20, 'RESEARCH',   'DALLAS');
    INSERT INTO DEPT VALUES (30, 'SALES',      'CHICAGO');
    INSERT INTO DEPT VALUES (40, 'OPERATIONS', 'BOSTON');

<br/>

    CREATE TABLE T1 (ID INTEGER);

<br/>

    INSERT INTO T1 VALUES (1);

<br/>

    CREATE TABLE T10 (ID INTEGER);

<br/>

    INSERT INTO T10 VALUES (1);
    INSERT INTO T10 VALUES (2);
    INSERT INTO T10 VALUES (3);
    INSERT INTO T10 VALUES (4);
    INSERT INTO T10 VALUES (5);
    INSERT INTO T10 VALUES (6);
    INSERT INTO T10 VALUES (7);
    INSERT INTO T10 VALUES (8);
    INSERT INTO T10 VALUES (9);
    INSERT INTO T10 VALUES (10);

<br/>

    CREATE TABLE T100 (ID INTEGER);

<br/>

    insert into t100 values (1);
    insert into t100 values (2);
    insert into t100 values (3);
    insert into t100 values (4);
    insert into t100 values (5);
    insert into t100 values (6);
    insert into t100 values (7);
    insert into t100 values (8);
    insert into t100 values (9);
    insert into t100 values (10);
    insert into t100 values (11);
    insert into t100 values (12);
    insert into t100 values (13);
    insert into t100 values (14);
    insert into t100 values (15);
    insert into t100 values (16);
    insert into t100 values (17);
    insert into t100 values (18);
    insert into t100 values (19);
    insert into t100 values (20);
    insert into t100 values (21);
    insert into t100 values (22);
    insert into t100 values (23);
    insert into t100 values (24);
    insert into t100 values (25);
    insert into t100 values (26);
    insert into t100 values (27);
    insert into t100 values (28);
    insert into t100 values (29);
    insert into t100 values (30);
    insert into t100 values (31);
    insert into t100 values (32);
    insert into t100 values (33);
    insert into t100 values (34);
    insert into t100 values (35);
    insert into t100 values (36);
    insert into t100 values (37);
    insert into t100 values (38);
    insert into t100 values (39);
    insert into t100 values (40);
    insert into t100 values (41);
    insert into t100 values (42);
    insert into t100 values (43);
    insert into t100 values (44);
    insert into t100 values (45);
    insert into t100 values (46);
    insert into t100 values (47);
    insert into t100 values (48);
    insert into t100 values (49);
    insert into t100 values (50);
    insert into t100 values (51);
    insert into t100 values (52);
    insert into t100 values (53);
    insert into t100 values (54);
    insert into t100 values (55);
    insert into t100 values (56);
    insert into t100 values (57);
    insert into t100 values (58);
    insert into t100 values (59);
    insert into t100 values (60);
    insert into t100 values (61);
    insert into t100 values (62);
    insert into t100 values (63);
    insert into t100 values (64);
    insert into t100 values (65);
    insert into t100 values (66);
    insert into t100 values (67);
    insert into t100 values (68);
    insert into t100 values (69);
    insert into t100 values (70);
    insert into t100 values (71);
    insert into t100 values (72);
    insert into t100 values (73);
    insert into t100 values (74);
    insert into t100 values (75);
    insert into t100 values (76);
    insert into t100 values (77);
    insert into t100 values (78);
    insert into t100 values (79);
    insert into t100 values (80);
    insert into t100 values (81);
    insert into t100 values (82);
    insert into t100 values (83);
    insert into t100 values (84);
    insert into t100 values (85);
    insert into t100 values (86);
    insert into t100 values (87);
    insert into t100 values (88);
    insert into t100 values (89);
    insert into t100 values (90);
    insert into t100 values (91);
    insert into t100 values (92);
    insert into t100 values (93);
    insert into t100 values (94);
    insert into t100 values (95);
    insert into t100 values (96);
    insert into t100 values (97);
    insert into t100 values (98);
    insert into t100 values (99);
    insert into t100 values (100);

<br/>

    -- зафиксировать изменения в базе
    commit;
