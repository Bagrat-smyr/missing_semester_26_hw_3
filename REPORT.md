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
