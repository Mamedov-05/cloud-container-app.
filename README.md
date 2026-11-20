# Cloud Container Demo

Практическая работа по Cloud Computing: контейнеризация Flask-приложения

## Требования
- Python 3.12+
- Docker
- Git

## Локальный запуск без Docker

python -m venv .venv
pip install -r requirements.txt
python app.py

Открыли `http://localhost:10000/` и `http://localhost:10000/health`.

## Сборка и запуск Docker
docker build -t cloud-container-app:1.0 .
docker run --rm -p 10000:10000 --name cloud-demo cloud-container-app:1.0
Проверьте:
- `http://localhost:10000/`
- `http://localhost:10000/health`

## Переменная окружения
Приложение использует `PORT`; значение по умолчанию — `10000`. Gunicorn слушает этот порт внутри контейнера.

## Публикация на GitHub
Создали публичный репозиторий и добавили файлы

## Ожидаемые ответы
`GET /` возвращает JSON с названием, версией, именем студента и сообщением.
`GET /health` возвращает `{"status":"ok"}` с HTTP 200.
