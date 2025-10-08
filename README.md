# Spends Tracker

## Spends Tracker Backend
![Python](https://img.shields.io/badge/python-3.9-blue?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/django-4.2.23-green?logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/DRF-3.16.0-9cf?logo=django&logoColor=white)
![Docker](https://img.shields.io/badge/docker-20.10-blue?logo=docker&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-blue)
![Build](https://img.shields.io/github/actions/workflow/status/USERNAME/REPO_NAME/docker-image.yml?branch=main)
![Coverage](https://img.shields.io/codecov/c/github/USERNAME/REPO_NAME/main)

**Spends Tracker Backend** — это ключевой микросервис для приложения по управлению и анализу личных финансов. Он предоставляет API для выполнения CRUD-операций с данными о доходах и расходах, а также включает аналитические и визуализационные инструменты на основе данных.

# Инструкция к запуску

- Каждая директория содержит свой собственный ридми
- Они крайне настоятельно рекомендуются к прочтению
- Запуск проекта воспроизводится посредством Docker-Compose

---

- Для запуска оздайте в корне 2 файла конфигурации
* .env.backend
* .env.bot

``` .env.backend
ADMINS = <telegram_id админов чере _>

DATABASE_URL = <Ссылка на облачную БД PostgresQL>

DEBUG = True

SECRET_KEY = <Секретный ключ джанго приложения>
```

``` .env.bot
ADMINS=<telegram_id админов чере _>

BASE_URL=http://backend:8000/ (адрес бекенда по умолчанию)

BOT_TOKEN=<токен вашего бота>

PORT=8000
```

- пропишите в корне проекта команду 
```zsh
docker compose -f 'docker-compose.yaml' up -d --build
```

# Spends Tracker Backend

**Spends Tracker Backend** — это ключевой микросервис для приложения по управлению и анализу личных финансов. Он предоставляет API для выполнения CRUD-операций с данными о доходах и расходах, а также включает аналитические и визуализационные инструменты на основе данных.

## Используемые технологии 🛠️

Проект разработан с использованием следующих ключевых технологий:

  * **Python 3.9**
  * **Django 4.2.23** и **Django REST Framework 3.16.0** для создания API.
  * **Pandas 2.3.1** для анализа данных.
  * **Matplotlib 3.9.4** и **Seaborn 0.13.2** для визуализации.
  * **Docker** для контейнеризации и упрощения развертывания.
  * **Gunicorn 23.0.0** как WSGI-сервер.
  * **drf-spectacular 0.28.0** для автоматической генерации документации OpenAPI.

## Структура проекта 📁

Проект имеет следующую структуру, разделенную на несколько приложений Django:

```
.
├── backend/
│   ├── analytics/        # Логика для аналитики и визуализации данных
│   ├── api/              # Основные CRUD-операции для доходов и расходов
│   ├── categories/       # Управление категориями доходов и расходов
│   ├── users/            # Управление пользователями
│   └── manage.py
├── docker-compose.yml
├── Dockerfile            # Инструкции для сборки Docker-образа
├── requirements.txt      # Список зависимостей
└── ...
```

-----

## API Документация 📜

API следует спецификации OpenAPI 3.0.3. Ниже приведено краткое описание доступных эндпоинтов, сгенерированное на основе твоего `openapi.yaml` файла.

### Аналитика

  * **`GET /analitics/stats/`**
      * Получение статистических данных о доходах и расходах.
  * **`GET /analitics/visual/`**
      * Получение визуального отчёта (графиков) по доходам и расходам.

### Управление данными (API)

  * **Расходы (`/api/expenses/`):**

      * **`GET /api/expenses/`**: Получить список всех расходов.
      * **`POST /api/expenses/`**: Создать новую запись о расходе.

  * **Отдельный расход (`/api/expenses/{id}/`):**

      * **`GET /api/expenses/{id}/`**: Получить детализацию по конкретному расходу.
      * **`PUT /api/expenses/{id}/`**: Обновить все поля расхода.
      * **`PATCH /api/expenses/{id}/`**: Частично обновить поля расхода.
      * **`DELETE /api/expenses/{id}/`**: Удалить запись о расходе.

  * **Доходы (`/api/incomes/`):**

      * **`GET /api/incomes/`**: Получить список всех доходов.
      * **`POST /api/incomes/`**: Создать новую запись о доходе.

  * **Отдельный доход (`/api/incomes/{id}/`):**

      * **`GET /api/incomes/{id}/`**: Получить детализацию по конкретному доходу.
      * **`PUT /api/incomes/{id}/`**: Обновить все поля дохода.
      * **`PATCH /api/incomes/{id}/`**: Частично обновить поля дохода.
      * **`DELETE /api/incomes/{id}/`**: Удалить запись о доходе.

### Категории

  * **`GET /categories/`**: Получить все доступные категории.
  * **`GET /categories/expences/`**: Получить категории расходов.
  * **`GET /categories/incomes/`**: Получить категории доходов.

### Пользователи

  * **`GET /users/user/`**: Получить список всех пользователей.
  * **`POST /users/user/`**: Создать нового пользователя.
  * **`GET /users/user/{id}/`**: Получить информацию о конкретном пользователе.
  * **`PUT /users/user/{id}/`**: Обновить все поля пользователя.
  * **`PATCH /users/user/{id}/`**: Частично обновить поля пользователя.
  * **`DELETE /users/user/{id}/`**: Удалить пользователя.

-----

## Установка и запуск 🚀

### Использование Docker

Для запуска проекта с помощью Docker выполните следующие шаги:

1.  **Сборка Docker-образа:**

    ```bash
    docker build -t spends_tracker_backend:latest .
    ```

2.  **Запуск контейнера:**

    ```bash
    docker run -d -p 8000:8000 --name spends_tracker_backend spends_tracker_backend:latest
    ```

3.  **Проверка работы:**
    После запуска вы можете получить доступ к API по адресу `http://localhost:8000/`.
