# plsql.ru


[![Build Status](https://travis-ci.org/plsql/plsql.ru.svg?branch=gh-pages)](https://travis-ci.org/plsql/plsql.ru)
[![Join the chat at https://gitter.im/oracle-dba-ru/Lobby](https://badges.gitter.im/oracle-dba-ru/Lobby.svg)](https://gitter.im/oracle-dba-ru/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Как скопировать и запустить plsql.ru на свой хост с использованием docker контейнера:

Инсталлируете docker, далее:

    $ docker pull marley/centos6-for-jekyll:latest
    $ docker run -i -t -p 80:8080 --name plsql_ru marley/centos6-for-jekyll:latest /bin/bash

<br/>

    $ source ~/.bash_profile
    $ cd /projects
    $ git clone --depth=1 https://bitbucket.org/plsql/plsql.ru .
    $ bundle
    $ JEKYLL_ENV=production bundle exec jekyll serve --host 0.0.0.0 --port 8080


<br/>

Остается в браузере подключиться к localhost
