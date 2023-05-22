Axelor Open Suite v7.0.1
================================

Axelor Open Suite снижает сложность и улучшает отзывчивость бизнес-процессов. Благодаря своей модульности, вы можете начать с небольшого набора функций и затем активировать другие модули по мере необходимости.

Axelor Open Suite включает следующие модули:

* Управление взаимоотношениями с клиентами (CRM)
* Управление продажами
* Финансовое и управление затратами
* Управление персоналом
* Управление проектами
* Управление запасами и цепочкой поставок
* Управление производством
* Многокомпанийность, многовалютность и многоязычность

Axelor Open Suite построена на основе [Axelor Open Platform](https://github.com/axelor/axelor-open-platform)

Технические требования
================================

* [OpenJDK 11](https://www.oracle.com/cis/java/technologies/javase/jdk11-archive-downloads.html)
* [PostgreSQL 11](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads) или новее
* [Apache Tomkat 9.0.75](https://tomcat.apache.org/download-90.cgi)

Установка
================================
1. Создайте новую папку "axelor-7.0.1" , в директории ../IdeaProjects/
2. Перейдите в новую созданную папку через терминал:
```bash
cd axelor-7.0.1
```
3. Для компиляции и запуска из исходного кода вам потребуется клонировать модули  
[Axelor Open Suite](https://github.com/axelor/axelor-open-suite) которые являются репозиторием подмодулей Git, с использованием следующих команд:

```bash
$ git clone git@github.com:axelor/open-suite-webapp.git
$ cd open-suite-webapp
$ git config --file=.gitmodules submodule.axelor-open-suite.url https://github.com/axelor/axelor-open-suite.git
$ git checkout master
$ git submodule init
$ git submodule update
$ git submodule foreach git checkout master
$ git submodule foreach git pull origin master
```
4. Подождите, пока подмодули обновятся до последних версий.
5. Создайте базу данных в PostgreSQL с названием 
```bash
axelor-open-suite
```
6. Добавьте пользователя к созданной базе данных с именем пользователя "axelor" и задайте пароль. 
```bash
usermname: axelor, password: ****** 
```
7. Откройте файл `axelor-config.application`  в папке
```bash
axelor-7.0.1\open-suite-webapp\src\main\resources
```
8. Настройте параметры базы данных:
```bash
db.default.url = jdbc:postgresql://localhost:5432/axelor-open-suite
db.default.user = axelor
db.default.password = postgres
```
9. 
