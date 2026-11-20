# Cloud Container Demo

Практическая работа по Cloud Computing: контейнеризация Flask-приложения и подготовка к развертыванию на Render.

## Требования
- Python 3.12+
- Docker
- Git

## Локальный запуск без Docker
```bash
python -m venv .venv
# Windows:
.venv\\Scripts\\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```
Откройте `http://localhost:10000/` и `http://localhost:10000/health`.

## Сборка и запуск Docker
```bash
docker build -t cloud-container-app:1.0 .
docker run --rm -p 10000:10000 --name cloud-demo cloud-container-app:1.0
```
Проверьте:
- `http://localhost:10000/`
- `http://localhost:10000/health`

## Переменная окружения
Приложение использует `PORT`; значение по умолчанию — `10000`. Gunicorn слушает этот порт внутри контейнера.

## Публикация на GitHub
Создайте публичный репозиторий и выполните:
```bash
git init
git add .
git commit -m "Initial cloud container app"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

## Развертывание на Render
1. В Render выберите **New → Web Service**.
2. Подключите публичный GitHub-репозиторий.
3. Выберите среду **Docker** и тариф **Free**.
4. Дождитесь статуса **Live**.
5. Проверьте адрес сервиса и путь `/health`.

## Ожидаемые ответы
`GET /` возвращает JSON с названием, версией, именем студента и сообщением.
`GET /health` возвращает `{"status":"ok"}` с HTTP 200.

Перед сдачей замените `Амирали [Фамилия]` в `app.py` на полные имя и фамилию.
