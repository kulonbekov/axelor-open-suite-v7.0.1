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
* [PostgreSQL 12](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads) или новее
* [Apache Tomkat 9.0.75](https://tomcat.apache.org/download-90.cgi)

Установка
================================
1. Необходимо скачать оболочку Axelor-ERP проекта по ссылке [open-suite-webapp](https://github.com/axelor/open-suite-webapp)
2. Разархивировать ZIP файл в папке с проектами
3. Перейти по ссылке в проводнике
```
open-suite-webapp-master\open-suite-webapp-master\modules
```
5. Удалить папку
```
axelor-open-suite
```
6. Внутри папки modules, запускаем git bash, ввести команду
```
git clone https://github.com/axelor/axelor-open-suite.git
```
7. После подождать , пока скачается все нужные модули для проекта
 
8. Создайте базу данных в PostgreSQL с названием 
```bash
axelor-open-suite
```
9. Откройте файл `axelor-config.application`  в папке
```bash
\open-suite-webapp\src\main\resources
```
10. Настройте параметры базы данных:
```bash
db.default.url = jdbc:postgresql://localhost:5432/axelor-open-suite
db.default.user = postgres
db.default.password = postgres
```
11. При сборке проекта версии от 7 версии, возникают две ошибки в подмодулях:
```bash
axelor-human-resource
axelor-project
```
12. Для успешной сборки проекта необходимо выполнить следующие изменения:

13 Откройте файл `package.json` в папке
```bash
axelor-7.0.1\open-suite-webapp\modules\axelor-open-suite\axelor-human-resource\src\main\axelor-react-timesheet
```
14 Исправит фрагмент кода `CI=false` в блоке "scripts":
```bash
"scripts": {
    "start": "node scripts/start.js",
    "build": "set \"CI=false\" && node scripts/build.js",
    "test": "node scripts/test.js --env=jsdom"
  },
```
15 Откройте файл `package.json` в папке
```bash
axelor-7.0.1\open-suite-webapp\modules\axelor-open-suite\axelor-project\src\main\task-editor
```
16 Исправить фрагмент кода `CI=false GENERATE_SOURCEMAP=false` в блоке "scripts":
```bash
"scripts": {
    "start": "react-scripts start",
    "build": "set \"CI=false\" && set \"GENERATE_SOURCEMAP=false\" && react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
```
17. После внесения этих изменений можно запустить сервер.

Запустите сервер
================================

1. Теперь настало время протестировать приложение. Приложение можно протестировать, 
создав пакет WAR и развернув его на сервере Tomcat или используя встроенный сервер Tomcat.

2. Встроенный сервер — это самый простой способ запустить приложение во время разработки.
3. Выполните следующую команду в терминале:
```bash
$ ./gradlew --no-daemon run
```
4. Через несколько секунд вы должны увидеть некоторые журналы и в конце что-то подобное:,
```bash
...
Ready to serve...

Running at http://localhost:8080/axelor-erp
```
5. Откройте предоставленную ссылку в вашем браузере и войдите, используя учетную запись 
администратора со следующими учетными данными: имя пользователя - admin, пароль - admin.
6. Второй способ: развернуть на сервере Tomkat:
7. Выполните следующую команду в терминале:
```bash
$ ./gradlew clean build
```
8. Убедитесь, что проект успешно собран и создан WAR-файл в папке
```bash
axelor-7.0.1\open-suite-webapp\build\libs
```
9. Установите Apache Tomcat на сервер или компьютер, где планируется развернуть приложение
10. Запустите сервер Apache Tomcat.
11. Скопируйте WAR-файл, полученный на предыдущем шаге, в директорию webapps внутри каталога установки Tomcat. Пример пути: 
```bash
<путь к установке Tomcat>/webapps.
```
12. Перейдите в каталог bin внутри каталога установки Tomcat.
13. Запустите скрипт startup.bat (для Windows) или startup.sh (для Linux/Unix) для запуска сервера Tomcat.
14. Откройте веб-браузер и введите URL-адрес приложения в следующем формате: 
```bash
http://localhost:8080/<имя приложения>.
```
Примечание: `<имя приложения>` - это имя WAR-файла без расширения .war.

15. Если приложение успешно развернуто, вы должны увидеть его главную страницу или другие страницы, предоставляемые приложением.

Примечания:
* `Убедитесь, что порт 8080 не занят другими приложениями или процессами.`
* `При необходимости, настройте доступные ресурсы, базы данных или конфигурацию приложения в соответствии с требованиями вашего проекта.`

