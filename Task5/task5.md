Задание 5. Управление трафиком внутри кластера Kubertnetes

Создание подов:

```bash

kubectl run front-end-app --image=nginx --labels role=front-end --expose --port 80

kubectl run back-end-api-app --image=nginx --labels role=back-end-api --expose --port 80

kubectl run admin-backend-api-app --image=nginx --labels role=admin-back-end-api --expose --port 80

kubectl run admin-front-end-app --image=nginx --labels role=admin-front-end --expose --port 80

```

Тестируем:

Должно работать ```kubectl exec -it front-end-app -- curl -s --connect-timeout 3 http://back-end-api-app```

Не должно работать ```kubectl exec -it front-end-app -- curl -s --connect-timeout 3 http://admin-back-end-api-app```

Должно работать ```kubectl exec admin-front-end-app -- curl -s --connect-timeout 3 http://admin-back-end-api-app```

Не должно работать ```kubectl exec admin-front-end-app -- curl -s --connect-timeout 3 http://back-end-api-app```