# TODO-сервис

## Описание

Простой веб-сервис, позволяющий создавать, хранить и управлять задачами пользоватей.
Поддерживается одновременная работа нескольких пользователей. Каждый пользователю доступны только задачи, созданные им.

API реализован на библиотеке FastAPI, хранение данных в SQLite.

## Как запустить

Все настройки приведены для запуска на локальной машине.
Если запустить с указанными здесь настройками, сервис будет доступен по адресу http://localhost:8000/

Документация и веб-интерфейс, предоставляемые фреймворком FastAPI доступны по адресу http://localhost:8000/docs

### Локально

1. Скопировать любым способом файлы проекта из каталога src
2. Установить зависимости из файла requirements.txt
```bash
pip install -r requirements.txt
```
3. Запустить веб сервер с приложением из каталога проекта src
```bash
uvicorn main:app --host 0.0.0.0 --port 80
```
### В Docker

#### Вариант 1. Собрать локальный образ

Собратьь образ локально:
```bash
docker build -t todo-sqlite:latest .
```
Создать именованный том:
```bash
docker volume create todo_data
```
Запустить контейнер с томом:
```bash
docker run -d -p 8000:80 -v todo_data:/app/data todo-sqlite:latest
```

#### Вариант 2. Из образа, опубликованного на Docker hub

Образ опубликован на [Docker hub](https://hub.docker.com/repository/docker/alexanderanv/todo-sqlite/general)

Скачать образ:
```bash
docker pull alexanderanv/todo-sqlite:latest
```
Создать именованный том:
```bash
docker volume create todo_data
```

Запустить контейнер с томом:
```bash
docker run -d -p 8001:80 -v todo_data:/app/data alexanderanv/todo-sqlite:latest
```
