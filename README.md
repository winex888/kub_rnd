# kub_rnd
Публикация образа в реестре
```
docker build -t safanasev/docs_app:0.1 .
docker run f88b666f2e1d
docker commit 3b671d9a0894  safanasev/docs_app:0.1
docker push safanasev/docs_app:0.1
```

Посмотреть расширенную информацию по поду

minikube kubectl -- get pod -o wide
Посмотреть объекты endpoint
minikube kubectl -- get ep

Запуск и удаление пода для тестирования сети
minikube kubectl -- run -t -i --rm --image amouat/network-utils test bash
