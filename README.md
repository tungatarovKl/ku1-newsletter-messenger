# Steps 

## Файловая структура:
- build = директория для поднятия проекта
- build/dev = среда разработки- локальная база данных в докере
- build/prod = продовая среда. используется существующуя база
- cmd = main файлы сервисов
- cmd/api = main файл сервиса рассылки
- cmd/bot = main файл сервиса регистрации пользователей
- config = конфиги и функция чтения конфигов
- config/dev.toml = конфиг для среды разработки 
- config/prod.toml = конфиг для прод среды
- internal = пакеты, которые доступны только внутри программы, недоступные извне
- internal/models = хранит структуры объектов (entities) и подключения базы данных
- internal/controllers = контроллеры для API
- internal/bot = логика телеграм- бота
- **Файлы базы данных (конфиги и данные) хранятся персистентно на docker volume**

Команда для очистки базы:
```
docker volume rm dev_messenger-mysql-data
```
## Инициализировать библиотеки
```shell
go mod vendor
```
## Указать телеграм-токен config/local.toml (создается через bot-father)
## Поднять сервис и БД в докере
```shell
cd ./build/dev
docker-compose up -d
```
## Создать таблицы в базе данных
Миграция: ./build/dev/DatabaseCreation.sql
## Создать токен для админки в таблице tokens
