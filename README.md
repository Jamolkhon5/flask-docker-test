# Flask Docker Test

Выполнение тестового задания для демонстрации работы с Docker и Flask.

## Описание проекта

Проект включает два задания:

1. Docker образ для простого Flask API с эндпоинтом `/ping`
2. Docker Compose конфигурация с Flask и Redis для подсчета посещений через эндпоинт `/count`

## Структура проекта

```
flask-docker-test/
├── app.py              # Flask приложение с эндпоинтами /ping и /count
├── requirements.txt    # Зависимости Python
├── Dockerfile         # Конфигурация Docker образа
├── docker-compose.yaml # Конфигурация для запуска двух контейнеров
└── README.md          # Этот файл
```

## Установка и запуск

1. Клонируйте репозиторий:
```bash
git clone <repository-url>
cd flask-docker-test
```

2. Создайте виртуальное окружение и установите зависимости:
```bash
python -m venv .venv
.venv\Scripts\activate  # На Windows
# или
source .venv/bin/activate  # На Linux/Mac

pip install flask redis
```

3. Создайте файл requirements.txt:
```bash
pip freeze > requirements.txt
```

4. Запустите проект через Docker Compose:
```bash
docker-compose up --build
```

## Тестирование

### Проверка эндпоинта /ping
```bash
curl http://localhost:5000/ping
```
Ожидаемый ответ:
```json
{"status": "ok"}
```

### Проверка эндпоинта /count
```bash
curl http://localhost:5000/count
```
Ожидаемый ответ:
```json
{"count": 1}
```

Повторные запросы будут увеличивать счетчик.

### Тестирование через Postman

1. Создайте GET запрос на `http://localhost:5000/ping`
2. Создайте GET запрос на `http://localhost:5000/count`  
3. Отправляйте запросы и проверяйте ответы

## Остановка контейнеров

```bash
docker-compose down
```

## Возможные проблемы

Если порт 6379 уже занят на вашей машине, убедитесь, что маппинг порта Redis удален из docker-compose.yaml.