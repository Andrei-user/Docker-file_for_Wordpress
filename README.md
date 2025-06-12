# Контейнеризированная среда: WordPress + MySQL + phpMyAdmin

Этот проект использует `docker-compose` для быстрого развёртывания системы управления контентом WordPress с базой данных MySQL и интерфейсом администрирования phpMyAdmin.

## Состав системы

- **WordPress** (`wordpress:6.8`) — последняя актуальная версия CMS.
- **MySQL** (`mysql:8.4`) — система управления базами данных.
- **phpMyAdmin** (`phpmyadmin:5.2`) — веб-интерфейс для управления MySQL.

## Конфигурация

Все чувствительные данные (логины, пароли, имена БД) вынесены в `.env` файл и не хранятся напрямую в `docker-compose.yml`.

Примеры переменных в `.env`

```dotenv
MYSQL_ROOT_PASSWORD=rootpass
MYSQL_DATABASE=wordpress
MYSQL_USER=wp_user
MYSQL_PASSWORD=wp_pass

WORDPRESS_DB_NAME=wordpress
WORDPRESS_DB_USER=wp_user
WORDPRESS_DB_PASSWORD=wp_pass

WORDPRESS_PORT=4000
PHPMYADMIN_PORT=4001

## Особености

Настройки подключения WordPress к MySQL заданы заранее — ручная настройка через UI не требуется.

phpMyAdmin автоматически подключается к MySQL, без необходимости указывать хост.

Добавлен healthcheck для MySQL — WordPress и phpMyAdmin начнут работать только после полной инициализации базы данных.



## Запуск
Создайте .env файл рядом с docker-compose.yml

Запустите проект:


``` docker-compose up -d ```

Перейдите в браузере:

WordPress: http://localhost:4000

phpMyAdmin: http://localhost:4001

## Остановка

``` docker-compose down ```