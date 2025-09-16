Задание 4. Защита доступа к кластеру Kubernetes

1. Запускаем minikube командой ```minikube start```
2. Создаем пользователей kubectl ```apply -f users.yaml```
3. Создаем роли ```kubectl apply -f roles.yaml```
4. Линкуем роли с пользователями ```kubectl apply -f user-role.yaml```
