## Новый Джанго-проект
1. Создаем репозиторий на github (https://github.com/mayor86/planner)
2. Создаем новый проект в PyCharm
![[Pasted image 20230917185023.png|300]]
3. Связываем с репозиторием в github:

> [!Последовательность команд]
> git init
> git remote add origin git@github.com:mayor86/planner.git
> git git add .
> git  git commit -m "init django-project"
> git push или git push --set-upstream origin main  
4. Устанавливаем пакет джанго **pip install django**
5.  Создаем новый Джанго проект python -m django startproject planner
![[Pasted image 20230917200933.png| 300]]
	**manage.py** - все, что нужно для управления проекта в Джанго (все идет через него)
	**asgi.py** - для запуска асинхронного веб-сервера на основе Джанго
	**settings.py** - файл настроек Джанго-проекта
	**urls.py** - url, которые обрабатываются
6.  cd planner
7. python manage.py runserverw


## Новое приложение Django app
1. **./manage.py startapp tasks**
2. Добавляем в INSTALLED_APPS tasks
3. Выполняем миграции **./manage.py makemigrations**
4. Накатываем миграции на БД **./manage.py migrate**

## Создание пользователя для Админки
1. В терминале выполняем python manage.py createsuperuser
## Регистрация модели в админке Джанго
1. Зайти в admin.py, написать код:

```
from django.contrib import admin  
from .models import Task  
  
# Register your models here.  
admin.site.register(Task)
```
Тут регистрируется модель Task
![[Pasted image 20230919184135.png|350]]
## Postgres в Docker
1. docker pull postgres (скачиваем образ)
2. docker run --name planner-16.0 -p 5432:5432 -e POSTGRES_PASSWORD=Siebel811 -d postgres:16.0
(Запускаем новый образ с паролем, переименовываем его в planner, выставляем порт наружу)
![[Pasted image 20230925204832.png]]
3. Установка pip install psycopg2-binary