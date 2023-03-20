# nginx ingress controller

- alb ingress https://github.com/quickbooks2018/aws-eks-blueprints

- Supported Versions table https://github.com/kubernetes/ingress-nginx/

- helm repo add
```helm
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
```

- helm repo list
```helm
helm repo list
helm search repo ingress-nginx
```

- Github
- https://github.com/kubernetes/ingress-nginx



- Charts
- https://github.com/kubernetes/ingress-nginx/tree/main/charts/ingress-nginx


- Values yaml
- https://github.com/kubernetes/ingress-nginx/blob/main/charts/ingress-nginx/values.yaml


- Deploy
- https://kubernetes.github.io/ingress-nginx/deploy/

- Kind Nginx Ingress controller
```kind
kubectl apply -f kind-nginx-ingress-controller.yaml
```

- Sample Application Setup with Helm
```helm
helm create hello
```


- Update values.yaml
- Update Image repo to quickbooks2018/green & tag:latest
- Enable Ingress & Update className: "external-nginx"

- helm app dry-run
```helm
helm template -f hello/values.yaml --namespace app --create-namespace hello/ --dry-run
```

- helm install app
```helm
helm upgrade --install hello -f hello/values.yaml --namespace app --create-namespace hello/ --wait
```

- helm create hello2

- helm install hello2

```helm
helm upgrade --install hello2 -f hello2/values.yaml --namespace app2 --create-namespace hello2/ --wait
```

- Ingress Classes
```ingress
kubectl get ingressclasses
```

- SSH Tunnel for Kubernes API Access
```ssh
ssh -NL 8443:0.0.0.0:8443 cloud_user@<IP>
```

- SSH Tunnel for Ingress Access
```ssh
ssh -NL 80:0.0.0.0:80 cloud_user@<IP>
```
