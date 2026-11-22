# ДЗ № 3 — Docker

## Этап 1. Один контейнер

Образ собран на основе python:3.13-slim.

Параметры запуска:
- Порт: 8080:8000
- GREETING: Hello from Bagrat!
- STORAGE: sqlite

## Результаты проверки

| Запрос | Результат |
| --- | --- |
| GET / | count = 0 |
| POST /increment | count = 1 |
| POST /increment | count = 2 |
| GET / | count = 2 |
| GET /healthz | HTTP 200 |
| GET /readyz | HTTP 200 |

Логи приложения сохранены в docker-logs.txt.

## Этап 2. Docker Compose и сохранение данных

Приложение запускается через compose.yaml.

Настройки:
- APP_PORT и GREETING задаются через .env
- Пример настроек находится в .env.example
- STORAGE=sqlite
- Именованный volume counter_data подключён к /data

### Проверка сохранения счётчика

Команды:

docker compose up -d --build
curl -fsS http://127.0.0.1:8080/
curl -fsS -X POST http://127.0.0.1:8080/increment
docker compose down
docker compose up -d
curl -fsS http://127.0.0.1:8080/

Результаты:
- Начальное значение: count = 0
- После POST: count = 1
- После удаления и пересоздания контейнера: count = 1

Данные сохранились благодаря именованному volume.
