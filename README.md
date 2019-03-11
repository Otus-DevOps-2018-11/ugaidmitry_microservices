# ugaidmitry_microservices
udmitry microservices repository

Д.З 14

   -  Установлен Docker
   -  Запущен первый контейнер "Hello world!"
   -  Ознакомился с командами (контейнеры + образы).
   -  Создан образ из запущенного контейнера.

Д.3 15


   -  создал новый проект в GCP (docker-)
   -  в новом проекте GCP создал хост с использованием docker-machine
   -  создал контейнер reddit
   -  проверил его работоспособность
   -  контейнер загружен на DockerHub

ДЗ  16

Скачан архив reddit-microservices и добавлены докерфайлы. 
ADD поменял  на COPY.
Собрал контейнеры.

docker build -t json1/post:1.0 ./post-py
docker build -t json1/comment:1.0 ./comment
docker build -t json1/ui:1.0 ./ui

В процессе сборки исправлен Dockerfile для post-py 
(скачал недостающие пакеты)
Создал сеть для приложения docker network create reddit
Запустил  контейнеры

docker run -d --network=reddit --network-alias=post_db --network-alias=comment_db mongo:latest
docker run -d --network=reddit --network-alias=post json1/post:1.0
docker run -d --network=reddit --network-alias=comment json1/comment:1.0
docker run -d --network=reddit -p 9292:9292 json1/ui:1.0

Контейнер с ui пересобран новым Dockerfile
Создан Docker volume docker volume create reddit_db
Контейнеры запущены снова с учетом изменений:

docker run -v reddit_db:/data/db -d --network=reddit --network-alias=post_db --network-alias=comment_db mongo:latest
docker run -d --network=reddit --network-alias=post json1/post:1.0
docker run -d --network=reddit --network-alias=comment json1//comment:1.0
docker run -d --network=reddit -p 9292:9292 json1/ui:2.0

Проверил работу приложения

Д.З 17

В процессе сделано:

- Запущены контейнеры с разными встроенными драйверами (none, host, bridge)

- Параматезирован docker-compose.yml


Д.З 19

В процессе сделано:

- установил gitlab
- сконфигурировал раннеры
- создал первый пайплайн


