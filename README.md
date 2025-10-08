# Spends Tracker


## Spends Tracker Backend

![Python](https://img.shields.io/badge/python-3.9-blue?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/django-4.2.23-green?logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/DRF-3.16.0-9cf?logo=django&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-2.3.1-blue?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/matplotlib-3.9.4-orange?logo=matplotlib&logoColor=white)
![Seaborn](https://img.shields.io/badge/seaborn-0.13.2-4B0082?logo=seaborn&logoColor=white)
![Gunicorn](https://img.shields.io/badge/gunicorn-23.0.0-blue?logo=python&logoColor=white)
![drf-spectacular](https://img.shields.io/badge/drf--spectacular-0.28.0-purple?logo=django&logoColor=white)
![Docker](https://img.shields.io/badge/docker-20.10-blue?logo=docker&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-blue)

## Spends Tracker Bot 🤖

![Python](https://img.shields.io/badge/python-3.9-blue?logo=python&logoColor=white)
![aiogram](https://img.shields.io/badge/aiogram-3.0-blue?logo=telegram&logoColor=white)
![aiohttp](https://img.shields.io/badge/aiohttp-3.9-blue?logo=python&logoColor=white)
![pydantic](https://img.shields.io/badge/pydantic-2.2-blue?logo=python&logoColor=white)
![Docker](https://img.shields.io/badge/docker-20.10-blue?logo=docker&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-blue)


**Spends Tracker Bot** — это Telegram-бот, разработанный для удобного и быстрого отслеживания личных финансов. С его помощью вы можете регистрировать свои расходы, управлять категориями трат, а также получать аналитику, чтобы лучше понимать, куда уходят ваши деньги.

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


  # Spends Tracker Bot

## Описание проекта 🤖

**Spends Tracker Bot** — это Telegram-бот, разработанный для удобного и быстрого отслеживания личных финансов. С его помощью вы можете регистрировать свои расходы, управлять категориями трат, а также получать аналитику, чтобы лучше понимать, куда уходят ваши деньги.

Бот является клиентской частью системы, взаимодействующей с внешним бэкенд-сервисом для хранения и обработки данных.

## Возможности 💡

  * **Учёт расходов:** Быстрое добавление новых трат с указанием суммы и категории.
  * **Управление категориями:** Добавление, изменение и удаление категорий расходов.
  * **Аналитика:** Получение статистики и отчётов по расходам за определённые периоды.
  * **Безопасность:** Аутентификация пользователя через Telegram ID.

-----

## Технологии 🛠️

Проект разработан на основе асинхронного фреймворка **`aiogram`** и использует следующие ключевые библиотеки:

  * **`aiogram`**: Основной фреймворк для создания Telegram-бота.
  * **`aiohttp`**: Асинхронная библиотека для выполнения HTTP-запросов к бэкенду.
  * **`python-dotenv`**: Для управления переменными окружения.
  * **`aiofiles`**: Для асинхронной работы с файлами.
  * **`pydantic`**: Для валидации данных.

Полный список зависимостей находится в файле `requirements.txt`.

-----

## Структура проекта 📂

```
.
├── app
│   ├── database             # Модули для работы с базами данных (если используются)
│   ├── filters              # Кастомные фильтры для aiogram
│   ├── handlers             # Обработчики команд, сообщений и коллбэков
│   │   ├── handlers.py      # Основные обработчики
│   │   ├── router.py        # Роутеры для разделения логики
│   │   └── templates.py     # Шаблоны для ответов бота
│   ├── keyboards            # Клавиатуры (инлайн и Reply)
│   │   ├── answer.py        # Reply-клавиатуры
│   │   └── inline.py        # Inline-клавиатуры
│   ├── middlewares          # Кастомные Middleware, например, для антифлуда
│   │   └── antiflud.py
│   ├── requests             # Функции для взаимодействия с бэкендом
│   │   ├── delete_account.py # Удаление аккаунта
│   │   ├── get_cat_error.py  # Обработка ошибок категорий
│   │   ├── get_categories.py # Получение категорий
│   │   └── login.py          # Авторизация пользователя
│   └── states               # FSM-состояния для сценариев
│       └── states.py
├── main.py                  # Точка входа в приложение
├── README.md                # Этот файл
├── requirements.txt         # Список зависимостей
└── venv                     # Виртуальное окружение
```

-----

## Установка и запуск 🚀

1.  **Клонируйте репозиторий:**
    ```bash
    git clone https://github.com/ваш_юзернейм/название_репозитория.git
    cd название_репозитория
    ```
2.  **Создайте и активируйте виртуальное окружение:**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```
3.  **Установите зависимости:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Настройте переменные окружения:**
    Создайте файл `.env` в корневой директории проекта и добавьте в него следующие переменные:
    ```
    BOT_TOKEN="ВАШ_API_ТОКЕН_БОТА"
    BASE_URL="АДРЕС_ВАШЕГО_БЭКЕНД_СЕРВИСА"
    ```
5.  **Запустите бота:**
