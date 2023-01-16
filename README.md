```
brew install minikube
mv .minikube ~/goinfre
ln -s ~/goinfre/.minikube ~/.minikube

minikube status
minikube start
minikube stop

brew install helm
```

Использование чужих чартов

```
helm repo add grafana https://grafana.github.io/helm-charts  # Добавляем репозиторий Хельм-Чартов
helm install grafana grafana/grafana                # Устанавливаем релиз grafana
kubectl get pods -w                                 # Пьем чай, пока Под Графаны не будет Running
kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
                                                    # Узнаем пароль от учетки admin
export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=grafana,app.kubernetes.io/instance=grafana" -o jsonpath="{.items[0].metadata.name}")
kubectl --namespace default port-forward $POD_NAME 3000
                                                    # Делаем проброс портов и заходим в браузер на  localhost:3000

Полезные инструменты

```
brew install aylei/tap/kubectl-debug
kubectl-debug declarative-deployment-5c74cc699f-gx9f4 --agentless=true --port-forward=true --agent-image=cr00z/debug-agent:v0.1
```