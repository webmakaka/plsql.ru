# [plsql.ru](https://plsql.ru) исходные коды

<br/>

### Запустить plsql.ru на своем в хосте в Ubuntu. (Должен быть установлен docker)

    # vi /etc/systemd/system/plsql.ru.service

Insert code from plsql.ru.service

    # systemctl enable plsql.ru.service
    # systemctl start plsql.ru.service
    # systemctl status plsql.ru.service

http://localhost:4006
