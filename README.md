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

# 👤 Автор

- Telegram: [@dianabol_metandienon_enjoyer](https://t.me/dianabol_metandienon_enjoyer)
- Email: segunperkele@gmail.com
- GitHub: github.com/Segun228