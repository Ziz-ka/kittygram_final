# Kittygram

Kittygram — это веб-приложение для публикации фотографий котов с указанием их достижений. Пользователи могут зарегистрироваться, добавлять, редактировать и удалять карточки своих питомцев, просматривать карточки других пользователей, а также оставлять лайки.

Проект создан в учебных целях для отработки навыков контейнеризации, настройки CI/CD и развёртывания многосервисных приложений.

## Основные возможности

- Регистрация и аутентификация пользователей (Djoser, TokenAuthentication).
- Добавление, редактирование и удаление карточек котов.
- Просмотр списка всех котов с пагинацией.
- Просмотр детальной информации о коте.
- Загрузка фотографий котов.
- Административная панель Django для управления данными.

## Стек технологий

- **Backend**: Python 3.10, Django 3.2, Django REST Framework, Djoser, Gunicorn.
- **Frontend**: React, JavaScript, HTML5, CSS3.
- **База данных**: PostgreSQL 13.
- **Веб-сервер**: Nginx (выступает как обратный прокси и сервер статики).
- **Контейнеризация**: Docker, Docker Compose.
- **CI/CD**: GitHub Actions (автоматическое тестирование, сборка и пуш образов в Docker Hub).

## Требования

- Установленный [Docker](https://www.docker.com/) и [Docker Compose](https://docs.docker.com/compose/).
- Свободные порты: `9000` (для Kittygram), `8000` (для Taski, если запускается параллельно).

## Установка и запуск

### 1. Клонирование репозитория

```bash
git clone https://github.com/Ziz-ka/kittygram_final.git
cd kittygram_final
```

### 2. Настройка переменных окружения

```ini
# Django
SECRET_KEY=ваш_секретный_ключ
ALLOWED_HOSTS=localhost,127.0.0.1
TIME_ZONE=Europe/Moscow

# PostgreSQL
POSTGRES_USER=django_user
POSTGRES_PASSWORD=django_password
POSTGRES_DB=django_db
DB_HOST=db
DB_PORT=5432

# Статика и медиа (в контейнере)
STATIC_ROOT=/static
MEDIA_ROOT=/media
```

### 3. Запуск проекта

```bash
docker-compose up --build
```
При первом запуске выполните миграции и создайте суперпользователя:
```bash
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py createsuperuser
```

### 4. Доступ к приложению

Фронтенд: http://localhost:9000/
Админка: http://localhost:9000/admin/
API: http://localhost:9000/api/