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
1. Создать новую папку "axelor-7.0.1" , в директории ../IdeaProjects/
2. Перейдите к новой созданной папке через терминал
```bash
cd axelor-7.0.1
```
Чтобы скомпилировать и запустить из исходного кода, вам потребуется клонировать модули 
[Axelor Open Suite](https://github.com/axelor/axelor-open-suite) который является репозиторием подмодулей git, используя следующие команды:

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

You can find more detailed [installation instructions](https://docs.axelor.com/abs/5.0/install/index.html) on our documentation.
