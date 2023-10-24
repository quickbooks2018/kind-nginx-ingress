# nginx ingress controller

- alb ingress https://github.com/quickbooks2018/aws-eks-blueprints

- Supported Versions table https://github.com/kubernetes/ingress-nginx/

- metrics server installation
```bash
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
helm repo update
helm upgrade --install --set args={--kubelet-insecure-tls} metrics-server metrics-server/metrics-server --namespace kube-system
```

```nginx
 kubectl exec ingress-nginx-controller-6bccc5966-bdbjt -n ingress-nginx -- nginx -v
 ```

- helm repo add
```helm
helm ls
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm search repo ingress-nginx
helm show values ingress-nginx/ingress-nginx
helm search repo ingress-nginx/ingress-nginx --versions
helm show chart ingress-nginx/ingress-nginx --version 4.8.2
helm show readme ingress-nginx/ingress-nginx --version 4.8.2
helm show values ingress-nginx/ingress-nginx --version 4.8.2
helm show values ingress-nginx/ingress-nginx --version 4.8.2 > ingress-nginx-values.yaml
helm show all ingress-nginx/ingress-nginx --version 4.8.2
helm upgrade --install ingress-nginx ingress-nginx/ingress-nginx --version 4.8.2 --namespace ingress-nginx --create-namespace --values ingress-nginx-values.yaml
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
