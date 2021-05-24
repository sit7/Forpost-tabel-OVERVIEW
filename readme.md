Проекты данного репозитория размещены для возможности предметного разговора и ознакомления при трудоустройстве.

Проект формирования табеля учета рабочего времени на основе АПК из СКУД-терминала и сервера видеоаналитики Форпост.

Основное:
1) Терминал отправляет видеопоток на сервер Форпост, где тот определяется на хранение в соответствии с настройками
и анализируется (в данном проекте интересует модуль распознавания лиц)
2) Терминал также обладает функциями видеоаналитики и возможностью хранить образы, ассоциированные с персоналиями
3) Результат видеоаналитики на сервере хранятся в базе данных MariaDB (MySQL 10.1.47)
4) Существует возможность пересылать результат распознавания лиц терминалом на сервер

Таким образом существует возможность получения идентификации персоны двумя способами - на сервере и на терминале.
Вопрос использования и выбора одной из них - относится к области защиты персональных данных, технически можно выбирать.

Основная идея: формирование табеля учета рабочего времени на основе поступающей информации об идентификации, по принципу:
первое прохождение в течение суток - время прихода на работу, последнее прохождение - время ухода (терминал находится в зоне,
не позволяющей фиксировать направление)

Данные должны быть загружены на PostgreSQL - сервер под дальнейший вывод в веб-формате + экспорт в json - для дальнейшего экспорта в 1С

Установка драйверов подключения (чтобы открыть соединение к mySQL на postgreSQL) на Ubuntu:

sudo apt-get install libmysqlclient-dev

sudo apt-get install postgresql-11-mysql-fdw

а дальше уже - CREATE EXTENSION mysql_fdw; -- см. initialize.sql

