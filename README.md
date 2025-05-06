
# 📦 Архитектура и План Работы Бэкенда — Natalya App

## 🧱 Обзор Технологий
| Раздел             | Стек / Сервис                            |
|--------------------|------------------------------------------|
| Фреймворк          | Python FastAPI                           |
| Аутентификация     | Email + Пароль + SMS (через Aero SMS)    |
| Уведомления        | Firebase Cloud Messaging (FCM)           |
| База данных        | PostgreSQL                               |
| Хостинг            | Timeweb Cloud VPS                        |
| Документация       | FastAPI `/docs` и `/redoc`              |
| Безопасность       | JWT + OAuth2 + Rate Limiting             |
| Конфигурация       | `.env`, Pydantic, `python-decouple`      |
| Хранилище файлов   | Amazon S3 или Timeweb S3                 |
| Контейнеризация    | Docker + docker-compose                  |

---

## ✅ Основные Функции и Сроки

### 1. 👥 Аутентификация Пользователей *(2 дня)*
- Регистрация/вход через Email + Пароль
- Подтверждение по SMS
- JWT токены

### 2. 🔐 Безопасность *(1 день)*
- Хеширование паролей (bcrypt)
- Token Refresh
- CORS и Middleware

### 3. 🗂️ Эндпоинты API *(4 дня)*
- `auth.py`, `tasks.py`, `projects.py`, `contacts.py`, `notes.py`
- `priorities.py`, `pets.py`, `calendar.py`, `thoughts.py`
- `settings.py`, `notifications.py`, `store.py`, `inventory.py`

### 4. 🔔 Firebase Уведомления *(2 дня)*
- Сохранение `device_token`
- Отправка push через Firebase SDK

### 5. ☁️ Хранилище Файлов *(1 день)*
- Загрузка файлов в S3
- Подпись URL

### 6. 🐳 Docker и Деплой *(2 дня)*
- Dockerfile + docker-compose
- Timeweb VPS + Nginx + Certbot

---

## 🧱 Структура Проекта

```
app/
├── main.py
├── models/
├── schemas/
├── crud/
├── api/v1/endpoints/
├── services/         # FCM, SMS, S3
├── core/
├── dependencies/
├── tasks/
.env
Dockerfile
```

---

## 🚀 План Деплоя (Timeweb VPS)

1. Установка Docker и Nginx
2. Клонирование репозитория
3. Загрузка `.env` и запуск `docker-compose up -d`
4. Настройка HTTPS через Certbot

---

## 🛠️ Этапы Разработки

| Этап                          | Статус       | Время |
|-------------------------------|--------------|--------|
| Модели                        | ✅ Завершено  | 1 день |
| Схемы                         | ✅ Завершено  | 1 день |
| CRUD                          | ✅ Завершено  | 2 дня  |
| Эндпоинты                     | ✅ Завершено  | 4 дня  |
| Auth (JWT + SMS)              | 🔄 В процессе | 2 дня  |
| Уведомления (Firebase)        | 🔄 В процессе | 2 дня  |
| Интеграция S3                 | 🔄 Опционально| 1 день |
| Docker и деплой               | 🔜 Следующий  | 2 дня  |

---

## 📋 Необходимые Данные от Клиента

- API ключ AeroSMS и Sender ID
- Firebase server key
- Доступ к Timeweb (IP, SSH)
- Доступ к S3 хранилищу (если нужно)
- Подтверждение логики Premium функций
- Нужно ли подключение админки / панели?

---

## ✅ Статус Готовности

- Подключение фронтенда
- Документация API `/docs`
- Масштабирование через Gunicorn/Uvicorn
