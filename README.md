# Kittygram

Kittygram — это веб-приложение для публикации и управления контентом. В этом проекте реализованы возможности публикации рецептов, подписки на авторов и создания списков покупок.
## Стек технологий

![Django](https://img.shields.io/badge/Django-092E20?logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=github-actions&logoColor=white)

## Содержание

- [Описание проекта](#описание-проекта)
- [Стек технологий](#стек-технологий)
- [Установка и настройка](#установка-и-настройка)
- [Автоматизация и развертывание](#автоматизация-и-развертывание)
- [Работа с проектом](#работа-с-проектом)
- [Лицензия](#лицензия)

## Описание проекта

Проект включает следующие компоненты:
- **Backend**: Разработан на Django и использует PostgreSQL для хранения данных.
- **Frontend**: SPA-приложение на React, предоставляет пользовательский интерфейс.
- **Gateway**: Nginx используется для проксирования запросов между клиентом и сервером.
- **Docker**: Используется для контейнеризации всех компонентов приложения.

## Установка и настройка

1. **Клонируйте репозиторий:**
   ```bash
   git clone <URL-репозитория>
   cd <папка-репозитория>
   ```

2. **Настройте переменные окружения:**
   Создайте файл `.env` в корневой директории проекта и добавьте настройки для PostgreSQL:
   ```env
   DB_NAME=kittygram_db
   DB_USER=kittygram_user
   DB_PASSWORD=your_password
   DB_HOST=db
   DB_PORT=5432
   ```

3. **Запустите Docker Compose:**
   ```bash
   docker-compose up --build
   ```

   Это запустит все контейнеры (backend, frontend, db, и gateway) и поднимет приложение.

## Автоматизация и развертывание

Проект настроен для автоматического тестирования и развертывания с помощью GitHub Actions:
- Проверка кода на соответствие PEP8.
- Запуск тестов для фронтенда и бэкенда.
- Сборка Docker образов и отправка их на Docker Hub.
- Обновление образов на сервере и перезапуск приложения.
- Сборка статики и выполнение миграций.
- Уведомления о завершении деплоя в Telegram.

## Работа с проектом

1. **Запуск тестов:**
   ```bash
   docker-compose exec backend pytest
   docker-compose exec frontend npm test
   ```

2. **Переход к интерфейсу приложения:**
   После запуска контейнеров, приложение доступно по [http://localhost](http://localhost).

3. **Обновление статики:**
   ```bash
   docker-compose exec backend python manage.py collectstatic
   ```

4. **Миграции:**
   ```bash
   docker-compose exec backend python manage.py migrate
   ```
