# Домашнее задание к занятию «Базы данных» - Николай Копосов

### Инструкция по выполнению домашнего задания

### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/netology-code/sdb-homeworks/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

### Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, Первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).

### Решение 1:


Таблица "Сотрудники":

 - Идентификатор (integer, первичный ключ, serial),
 - Фамилия (varchar(50)),
 - Имя (varchar(50)),
 - Отчество (varchar(50)),
 - Оклад (integer, внешний ключ, ссылается на таблицу "Должность"),
 - Должность (integer, внешний ключ, ссылается на таблицу "Должность"),
 - Идентификатор структурного подразделения (integer, внешний ключ, ссылается на таблицу "Структурные подразделения"),
 - Дата найма (date),
 - Идентификатор проекта (integer, внешний ключ, ссылается на таблицу "Проекты"),
 - Контакты(numerik)

Таблица "Структурные подразделения":

 - идентификатор (integer, первичный ключ, serial),
 - Название подразделения (varchar(100)),
 - Адрес (integer, внешний ключ, ссылается на таблицу "Адрес")
 - Описание (text).

Таблица "Адрес":

 - идентификатор (integer, первичный ключ, serial),
 - Название филиала (varchar(100)),
 - Регион (integer, внешний ключ, ссылается на таблицу "Регион"),
 - Город (integer, внешний ключ, ссылается на таблицу "Город"),
 - Адрес (varchar(50)).
 

Таблица "Проекты":

 - идентификатор (integer, первичный ключ, serial),
 - Название проекта (varchar(100)),
 - Адрес (integer, внешний ключ, ссылается на таблицу "Адрес")
 - Описание (text),
 - Дата начала (date),
 - Дата окончания (date).
 
Таблица "Типы подразделений":

 - идентификатор (integer, первичный ключ, serial),
 - Название типа подразделения (varchar(100)),
 - Структурное подразделение (integer, внешний ключ, ссылается на таблицу "Структурное подразделение")
 - Менеджер Типа подразделений (integer, внешний ключ, ссылается на таблицу "Сотрудники").

Таблица "Должности":

 - идентификатор (integer, первичный ключ, serial),
 - Название должности (varchar(100)),
 - Тип подразделения (integer, внешний ключ, ссылается на таблицу "Типы подразделений"),
 - Структурное подразделение (integer, внешний ключ, ссылается на таблицу "Структурное подразделение")
 - Оклад (numeric),
 - Описание (text).

Таблица "Структурное подразделение":

 - идентификатор (integer, первичный ключ, serial),
 - Название типа подразделения (varchar(100)),
 - Адрес подразделения (integer, внешний ключ, ссылается на таблицу "Адрес")
 - Описание (text).

Таблица "Регион"

- идентификатор (integer, первичный ключ, serial),
- Название региона (varchar(100)),
- Описание (text),

Таблица "Город"

- идентификатор (integer, первичный ключ, serial),
- Название города (varchar(100)),
- Регион (integer, внешний ключ, ссылается на таблицу "Регион")