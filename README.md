https://github.com/OWNER/REPOSITORY/actions/workflows/WORKFLOW-FILE/badge.svg
# Проект kittygram_final
## Автор ##
Проект выполнен: Команда Яндекс Практикум, Чернышов Владислав
## Описание проекта и его задач ##
Проект kittygram_final представляет собой веб-приложение позволяющее пользователям создавать на нём свою учётную запись, а именно регистрироваться, авторизироваться, менять свой пароль. Главной возможнорстью проекта является способность создавать пост/запись о котах, а именно: Добавить его изображение, указать его достижения из доступных или придумать достижение самому, указать его возраст, цвет, а также год рождения. 
## Использованные технологии ##
В проекте **kittygram_final** за основу был взять фреймворк для разработки быстрых и безопасных веб-приложений и сайтов на языке Python - **Django**. Основная цель фреймворка — помочь разработчикам быстро и безопасно создавать серверную часть сайтов. Также данное приложение может быть развёрнуто как локально, так и на удалённом сервере при помоще **Docker**. **Docker** — это платформа с открытым исходным кодом для автоматизации разработки, доставки и развёртывания приложений.
## Развёртывание проекта локально 
### Этап 1: Клонирование репозитория
1) >git clone git@github.com:<имя пользователя>/kittygram_final.git
2) >cd <ваш путь файла>/kittygram_final/backend/
### Этап 2: Создание виртуального окружения и его активация
1) >python -m venv venv
2) >source venv/Scripts/activate
### Этап 3: Установка необходимых зависимостей 
1) >pip install -r requirements.txt
### Этап 4: Применение миграций
1) >python manage.py makemigrations
2) >python manage.py migrate
### Этап 5: Создание файла с переменными окружения (.env)
Необходимые пременные:
1) POSTGRES_USER
2) POSTGRES_PASSWORD
3) POSTGRES_DB
4) DB_HOST
5) DB_PORT
6) DEBUG
7) ALLOWED_HOSTS
8) SECRET_KEY
### Этап 6: Запуск сервера
1) >python manage.py runserver
## Развёртывание проекта на удалённом сервере
### Этап 1: Копирвоание файла docker-compose.production.yml на сервер в директорию с приложением:
scp /путь/к/локальному/файлу username@server_ip:/путь/к/удаленной/папке
### Этап 2: Создание в директории приложения файла с переменными окружения: (.env)
1) sudo nano .env
### Необходимые пременные:
1) POSTGRES_USER
2) POSTGRES_PASSWORD
3) POSTGRES_DB
4) DB_HOST
5) DB_PORT
6) DEBUG
7) ALLOWED_HOSTS
8) SECRET_KEY
### Этап 3: Установка на сервере docker и docker compose:
1) sudo apt update
2) sudo apt install curl
3) curl -fSL https://get.docker.com -o get-docker.sh
4) sudo sh ./get-docker.sh
5) sudo apt install docker-compose-plugin 
### Этап 4: Сборка контейнеров проекта:
1) sudo docker compose -f docker-compose.production.yml up -d
### Этап 5: Применение миграций, сбор статики и копирование статики
1) sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
2) sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic --no-input
3) sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
