---
layout: page
title: Очереди
description: Очереди
keywords: Очереди
permalink: /other/queue/
---

# Очереди

<br/>

Мне неактуально, разбирайтесь сами. Если готовы поразбираться и поделиться результатами, welcome!

<br/>

https://t.me/oracle_dba_ru/6090

<br/>

```sql
-- Создаём пользователя (можно пропустить)
create tablespace testqueue_tablespace DATAFILE 'D:\ORACLE\TESTQUEUE.DAT'
SIZE 20M REUSE AUTOEXTEND ON NEXT 2M MAXSIZE 1000M;

create USER testqueue IDENTIFIED BY "testqueue"
default tablespace testqueue_tablespace;

-- Даём гранты
grant create session to testqueue;
alter user testqueue quota unlimited on testqueue_tablespace;
grant create table to testqueue;
grant CREATE TRIGGER to testqueue;
grant create synonym to testqueue;
grant create sequence to testqueue;
grant create procedure to testqueue;
grant create type to testqueue;
grant create view to testqueue;
grant create materialized view to testqueue;
-- Работа с очередью
grant execute on DBMS_AQADM to testqueue;
grant execute on DBMS_AQ to testqueue;

/
-- Создаём тип для очереди
create or replace type QueueMessageType as object
(
  id     number,
  Param1 number,
  param2 number
)
/
begin
  -- Создаём таблицу для очереди
  dbms_aqadm.create_queue_table(queue_table => 'QUEUETABLE',
                                queue_payload_type => 'TESTQUEUE.QUEUEMESSAGETYPE');

  -- Создаём саму очередь
  dbms_aqadm.create_queue(queue_name => 'MSG_QUEUE',
                          queue_table => 'QUEUETABLE');

  -- заупускаем очередь
  dbms_aqadm.start_queue('MSG_QUEUE');
end;
/
-- Создаём обычную таблицу, где будем хранить все сообщения
create table MSGDATA
(
  id      NUMBER generated always as identity,
  paramid NUMBER not null,                       -- Параметры входящего сообщения
  param1  NUMBER not null,                       -- Параметры входящего сообщения
  param2  NUMBER not null,                       -- Параметры входящего сообщения
  result  NUMBER,                                -- Результат работы
  status  VARCHAR2(1) not null,                  -- Статус записи
  updated DATE not null,
  created DATE default sysdate not null
)
/
-- Создаем триггер на нашу таблицу
create or replace trigger msgdata_BI
  before insert or update on msgdata
  for each row
DECLARE
  enqueue_options    dbms_aq.enqueue_options_t;
  message_properties dbms_aq.message_properties_t;
  message_handle     RAW(16);
  message            queuemessagetype;
begin
  -- Время обновления записи
  :new.updated := sysdate;

  if inserting then
    :new.status  := 'N'; -- New

    -- Создаём сообщение для очерерди
    message := queuemessagetype(:new.paramid, :new.param1, :new.param2);

    -- Добавляем сообщение в очередь
    dbms_aq.enqueue(queue_name         => 'msg_queue',
                    enqueue_options    => enqueue_options,
                    message_properties => message_properties,
                    payload            => message,
                    msgid              => message_handle);
  end if;
end msgdata_BI;
/
-- Создаём процедуру где будем работать с очередью
create or replace procedure DoWork is
  dequeue_options    dbms_aq.dequeue_options_t;
  message_properties dbms_aq.message_properties_t;
  message_handle     RAW(16);
  message            queuemessagetype;
  vResult            number;
BEGIN
  -- Достаём запись из очереди
  DBMS_AQ.DEQUEUE(queue_name         => 'msg_queue',
                  dequeue_options    => dequeue_options,
                  message_properties => message_properties,
                  payload            => message,
                  msgid              => message_handle);

  -- Здесь обрабатываем наше сообщение
  -- ... много много логики
  vResult := message.param1 + message.param2;

  -- Сохраняем результат, обновляем статус, о том что сообщение обработано
  update msgdata
     set result = vResult,
         status = 'D' -- Done
   where paramid = message.id;

end DoWork;
/
-- Вставляем записи в нашу таблицу, они автоматически добавятся в очередь.
insert into msgdata(paramid, param1, param2) values(1, 10, 15);
insert into msgdata(paramid, param1, param2) values(2, 30, 30);
insert into msgdata(paramid, param1, param2) values(3, 100, 100);
/
-- Обрабатываем две записи из трёх
begin
  DoWork;
  DoWork;
end;
/
-- Проверяем результат
select * from msgdata;
```

<br/>

https://gist.github.com/dbobylev/64206405cc800fd9dc27077a50076a9b
