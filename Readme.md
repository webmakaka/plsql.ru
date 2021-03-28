# [plsql.ru](https://plsql.ru) исходные коды

<br/>

### Запустить plsql.ru на своем в хосте Ubuntu в режиме разработки. (Должен быть установлен docker и docker-compose)

```
$ docker-compose up
```

<br/>

Подключиться к localhost:80, чтобы посмотреть результаты.

<br/>

### Запустить plsql.ru на своем в хосте в Ubuntu как сервис. (Должен быть установлен docker)

<br/>

```
# vi /etc/systemd/system/plsql.ru.service
```

Вставить содержимое файла plsql.ru.service

```
# systemctl enable plsql.ru.service
# systemctl start plsql.ru.service
# systemctl status plsql.ru.service
```

http://localhost:4006

<br/>

### Контакты

Чтобы задать вопрос, добавить свои знания, исправить ошибки и неточности, пишите в телеграм <a href="//plsql.ru/chat/" rel="nofollow">чате</a>.
