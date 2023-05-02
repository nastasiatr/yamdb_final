# ЯП - Спринт 16 - CI и CD проекта api_yamdb. Python-разработчик (бекенд) (Яндекс.Практикум)
 

![example workflow](https://github.com/nastasiatr/yamdb_final/blob/master/.github/workflows/yamdb_workflow.yml/badge.svg)

## Описание 
Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории:«Книги», «Фильмы», «Музыка». Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»). Настроика для приложения Continuous Integration и Continuous Deployment, реализация:

автоматический запуск тестов,
обновление образов на Docker Hub,
автоматический деплой на боевой сервер при пуше в главную ветку main.
 
## Стек технологий: 
* Python 3.7 
* DRF (Django REST framework) 
* Django ORM 
* Docker 
* Gunicorn 
* nginx 
* Яндекс Облако(Ubuntu 18.04) 
* Django 3.2 
* PostgreSQL 
* GIT 
 
 
## Файлы для развёртывания инфраструктуры находятся в папке infra/. 
 
 * Dockerfile инструкция по созданию образа для контейнера. 
 * docker-compose.yaml инструкция для запуска нескольких контейнеров. 
 * settings.py указаны дефолтные значения для переменных из env-файла, ведь в env-файле хранится секретная информация, а ей не место в репозитории. Дефолтные значения нужны для успешного прохождения тестов на платформе. 
 
## Контейнеризация проекта: 
 
### Локальная установка 
 
1. Настройте среду ".env" в каталоге "infra_sp2/infra/.env". Для этого выполните команду: 
 
``` 
cp infra/.env.template infra/.env 
``` 
2. Измените значения в файле .env 
 
 
### Команды для запуска приложения в контейнерах 
В терминале, перейдите в каталог, в который будет загружаться приложение: 
``` 
cd  
``` 
Клонируйте репозиторий: 
``` 
git clone git@github.com:nastasiatr/infra_sp2.git 
``` 
Перейдите в каталог приложения, папку инфраструктуры: 
``` 
cd infra_sp2/infra/ 
``` 
Запустите docker-compose командой: 
``` 
docker-compose up 
``` 
Выполните миграции: 
``` 
sudo docker-compose exec web python manage.py migrate 
``` 
**Заполнить базу данных начальными данными (из резервной копии) можно по инструкции раздела ниже.** 
 
Создайте суперюзера (логин\почта\пароль): 
``` 
sudo docker-compose exec web python manage.py createsuperuser 
``` 
Соберите статические файлы: 
``` 
sudo docker-compose exec web python manage.py collectstatic --no-input  
``` 
* Теперь проект готов к запуску и доступен по адресу: http://localhost/api/v1 
* Доступ к панели администратора: http://localhost/admin/login/?next=/admin 
 
Остановить и удалить контейнеры, оставив образы: 
``` 
sudo docker-compose down  
``` 
### Команды для заполнения базы данных 
 
Чтобы сделать резервную копию базы данных выполните команду из директории infra_sp2\infra: 
 
``` 
sudo docker-compose exec web python manage.py dumpdata > fixtures.json 
```     
 
Чтобы скопировать файл базы данных в контейнер выполните команду из директории infra_sp2/infra: 
``` 
docker cp fixtures.json <id>:app/ 
```   
 
Подгрузите данные БД из директории infra\docker-compose.yaml: 
 
``` 
docker-compose exec web python manage.py loaddata fixtures.json 
``` 
 

Документация API YaMDb
Документация доступна по эндпойнту: http://localhost:8000/redoc/


### Автор работы: 
 
Трусова Анастасия (https://github.com/nastasiatr) 

