# Kittygram

Kittygram - это приложение для публикации карточек котиков. Проект состоит из
backend на Django REST Framework и frontend на React.

Пользователь может зарегистрироваться, войти в аккаунт, добавить карточку
котика, загрузить изображение, выбрать цвет, указать достижения, редактировать
карточки и просматривать список с пагинацией.

## Стек технологий

- Python 3.9, Django 3.2, Django REST Framework, Djoser
- PostgreSQL 13
- React 17
- Docker and Docker Compose
- Docker и Docker Compose
- Nginx gateway
- GitHub Actions
- Docker Hub

## Переменные окружения

Перед запуском создайте файл `.env` на основе `.env.example`:

```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
STATIC_ROOT=/static
MEDIA_ROOT=/media
DOCKERHUB_USERNAME=atskih
SECRET_KEY=change_me
DEBUG=False
TIME_ZONE=Europe/Moscow
ALLOWED_HOSTS=kittygram.atskih.ru,localhost,127.0.0.1
```

Для production замените `SECRET_KEY`, `POSTGRES_PASSWORD`,
`DOCKERHUB_USERNAME` и `ALLOWED_HOSTS` на реальные значения.

## Локальный запуск в контейнерах

Установите Docker Desktop или Docker Engine, затем выполните:

```bash
docker compose up -d --build
```

Локально Kittygram будет доступен через gateway:

```text
http://localhost:9000
```

Полезные команды:

```bash
docker compose ps
docker compose logs -f backend
docker compose down
```

## Данные для автотестов

В корне проекта должен быть файл `tests.yml` с публичными данными деплоя:

```yaml
repo_owner: atskih
kittygram_domain: https://kittygram.atskih.ru
taski_domain: https://taski.atskih.ru
dockerhub_username: atskih
```

## Проверки

Локальные проверки:

```bash
python -m ruff check backend
python -m ruff format --check backend
python -m pycodestyle --ignore=E501,W503 backend
python -m pytest tests/test_files.py
```

Полный запуск автотестов:

```bash
python -m pytest
```
