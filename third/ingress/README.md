kubectl apply -f deploy.yaml
kubectl create -f ingress.yaml
kubectl get deployment -n nginx-ingress
kubectl create -f ingress-rules.yaml
kubectl get ing

curl -H "Host: my.kubernetes.example" 101.1.1.1/webapp1
curl -H "Host: my.kubernetes.example" 101.1.1.1/webapp2