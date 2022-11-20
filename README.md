# Steps 

## Файловая структура:
- build = директория для поднятия проекта
- cmd = хранит пакеты, которые доступны извне
- cmd/api = main файл сервиса рассылки
- cmd/bot = main файл сервиса регистрации пользователей
- config = конфиги и функция чтения конфигов
- internal = пакеты, которые доступны только внутри программы, недоступные извне
- internal/models = хранит структуры объектов (entities) и подключения нашей базы данных к самому проекту.
- internal/controllers = контроллеры для API
- internal/bot = логика телеграм- бота
- **Файлы базы данных (настройки и данные) пробрасываются в папку ../ku1-newsletter-messenger-database,
т.е. создается директория на уровень выше директории проекта**
## Инициализировать библиотеки
```shell
go mod vendor
```
## Указать телеграм-токен config/local.toml
## При необходимости изменить параметры базы данных в config/local.toml и build_messenger/database/Dockerfile
## Поднять сервис и БД в докере
```shell
cd ./build
docker-compose up -d
```
## При необходимости создать таблицы в базе данных
Миграция: ./build/DatabaseCreation.sql
