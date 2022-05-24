## DJANGO AND POSTGRES

Создать образ:
```commandline
$ docker-compose build
```
После создания образа запустить контейнер:
```commandline
$ docker-compose up -d 
```
Проверить наличие ошибок в журналах:
```commandline
docker-compose logs -f
```
Создать новый образ и запустите два контейнера:
```commandline
$ docker-compose up -d --build
```
Запустите миграции:
```commandline
$ docker-compose exec web python manage.py migrate --noinput
```
Проверить, что таблицы Django по умолчанию были созданы:
```commandline
$ docker-compose exec db psql --username=hello_django --dbname=hello_django_dev
```
List of relations
```commandline
hello_django_dev=# \dt
hello_django_dev=# \q
```
 Команды в запущеныом контейнере:
```commandline
$ docker-compose exec web python manage.py flush --no-input
$ docker-compose exec web python manage.py migrate 
```
Разрешения файлов локально:
```commandline
$ chmod +x app/entrypoint.sh
```
Остановить все Docker контейнеры:
```commandline
$ docker stop $(docker ps -a -q)
```
Удалить все Docker контейнеры:
```commandline
$ docker rm $(docker ps -a -q)
# or
$ docker container prune
```
Удалить все Docker images:
```commandline
$ docker rmi $(docker images -q)
```