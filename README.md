# Пошаговая инструкция
Публикация образа в реестре
```
docker build -t safanasev/docs_app:0.1 .
docker run f88b666f2e1d
docker commit 3b671d9a0894  safanasev/docs_app:0.1
docker push safanasev/docs_app:0.1
```

Посмотреть расширенную информацию по поду
```
minikube kubectl -- get pod -o wide
```
Посмотреть объекты endpoint
```
minikube kubectl -- get ep
```
Запуск и удаление пода для тестирования сети
```
minikube kubectl -- run -t -i --rm --image amouat/network-utils test bash
```
Включение ingress в minikube
```
 minikube addons enable ingress-dns
 minikube addons enable ingress
```
Проверка что включено
```
minikube addons list
```

Добавьте следующую строку в конец `/etc/hosts` файла.
`172.17.0.15 localkube.info`

`
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install my-prometheus  prometheus-community/prometheus
helm install --name my-release prometheus-community/prometheus-adapter
export POD_NAME=$(kubectl get pods --namespace default -l "app=prometheus,component=server" -o jsonpath="{.items[0].metadata.name}")
kubectl --namespace default port-forward $POD_NAME 9090
`

 `kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.001; do wget -q -O- http://localkube.info/info; done"`

Использовать клиент прометеуса https://github.com/prometheus/client_python

собирать метрики `request_processing_seconds_count` и с помощью функции `rate` прометеуса,
расчитывать rps
`rate(http_requests_total{job="api-server"}[5m])`