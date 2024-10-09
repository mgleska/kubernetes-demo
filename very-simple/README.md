# Very simple with Minikube

### for Windows:

In `C:\Windows\System32\drivers\etc\hosts` add line:
```text
127.0.0.1 kubernetes.local
```

Run:
```bash
minikube start
minikube addons enable ingress

kubectl apply -f deployment.yaml

minikube tunnel
...
Ctrl-C
minikube stop
```

### for Linux:

Run:
```bash
minikube start
minikube addons enable ingress
minikube ip  # will show {MINIKUBE_IP} address assigned to Minikube
```

In `/etc/hosts` add line:
```text
{MINIKUBE_IP} kubernetes.local
```

Run:
```bash
kubectl apply -f deployment.yaml

...
minikube stop
```

### Testing:

API documentation:

    http://kubernetes.local/api.html
    http://kubernetes.local/api.yaml
    http://kubernetes.local/api.json

Sample query:

    curl --location 'http://kubernetes.local/order/address/list' --header 'Authorization: Bearer user-1'

    curl --location 'http://kubernetes.local/order/address/1' --header 'Authorization: Bearer user-1'

    curl --location 'http://kubernetes.local/order/order/1' --header 'Authorization: Bearer user-1'
