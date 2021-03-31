# [plsql.ru](https://plsql.ru) исходные коды

<br/>

### Запустить plsql.ru на своем в хосте Ubuntu в режиме разработки.

Инсталлируете <a href="//sysadm.ru/devops/containers/docker/setup/ubuntu/">docker</a> и docker-compose.

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

<br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://oracledba.net/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://plsql.ru/chat/">Телеграм чат</a>
