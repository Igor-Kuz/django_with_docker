# Dango with docker 
## Пример django проекта с POSTGRES, DOCKER и NGINX готового для деплоя.

### Инструменты разработки
 
**Стек:**

 - Python >= 3.9

- Django ==3.2.6

- POSTGRES

- DOCKER ==20.10.8

- NGINX

## Установка и запуск

##### 1) Открыть терминал или консоль и перейти в нужную Вам директорию

##### 2) Клонировать репозиторий и поставить звездочку)
    git clone https://github.com/Igor-Kuz/django_with_docker.git

##### 3) Создать виртуальное окружение

python3 -m venv venv
    
##### 4) Активировать виртуальное окружение

##### 5) В файле settings.py импортировать и добавить настройки для статики и медиа файлов

##### 5) Создать файлы окружения:
- .env.dev для разработки
- .env.prod для прода
- .env.prod.db для данных БД

##### 6) Запустить проект в докере

     docker-compose -f docker-compose.prod.yml up -d --build
     docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput
     docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear
##### 7) Проверить работу можно используя адрес http://localhost:1337/

##### 8)Остановить контенер можно используя команду
    
    docker-compose -f docker-compose.prod.yml down -v

##### 9) Просмотреть логи прод версии можно с помощью команды
    docker-compose -f docker-compose.prod.yml logs -f


##### 10)Проверить при разработке что значения для базы созданы данных можно с помощью команды
    docker volume inspect django-on-docker_postgres_data