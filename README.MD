 MERN Stack

**Важно!** Перед запуском `docker-compose` необходимо установить зависимости в каталогах `frontend-docker` и `backend-docker` и выполнить команду `npm run build`, в кажд
ом из каталогов соответственно. После чего можно запускать `docker-compose up -d`.

### Frontend
Находится в директории `frontend-docker`.
1. Запуск проекта 
```
npm start
```
2. Собрать проект
```
npm build
```

### Backend
Находится в директории `backend-docker`.
1. Запуск проекта 
```
npm start
```
2. Собрать проект
```
npm build
```

## Файл `docker-compose.yml`
1. Собрать образы.
```
docker-compose build
```

2. Запустить проект.
```
docker-compose up -d
```

**Обратите внимание!**

В `docker-compose.yml` прописаны healthcheck по ним можно ориентироваться для определния запущен сервис или нет.



## Gitlab CI
1.  Push repository on gitlab.com
2. Add runners with the following tags:
```
Runner1 (executor - docker).
	tags: build, docker, node 
Runner2(executor - shell).
	tags: build, shell
```

![](https://github.com/EricRoux/docker-mern/master/images/1.png)
