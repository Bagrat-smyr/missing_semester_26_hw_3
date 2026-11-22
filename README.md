# ДЗ № 3 — Docker

Приложение со счётчиком, работающее через Docker Compose и Redis.

Исходный код в папке app не изменялся.

## Запуск

1. Скопировать настройки: cp .env.example .env
2. Запустить: docker compose up -d --build --wait
3. Открыть: http://127.0.0.1:8080/

## Проверка

GET / — текущее значение счётчика.
POST /increment — увеличение счётчика.
GET /healthz — проверка работы приложения.
GET /readyz — проверка доступности Redis.

## Остановка

docker compose down

Данные Redis сохраняются в именованном volume redis_data.
Для сохранения данных не использовать down -v.

## Настройки

APP_PORT — внешний порт.
GREETING — приветствие.
STORAGE — redis.
REDIS_URL — redis://redis:6379/0

## Результаты проверок

Подробный отчёт находится в REPORT.md.
