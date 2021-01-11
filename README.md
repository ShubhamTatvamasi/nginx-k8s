# nginx-k8s

Deploy on k8s
```bash
kubectl apply -f .
```

Delete from k8s
```bash
kubectl delete -f .
```

Get node info
```bash
kubectl get nodes -o wide
```

open your node IP with 30080 port

---

Create a pod
```bash
kubectl run nginx --image=nginx:alpine --port=80 --expose

kubectl patch svc nginx \
  --patch='{"spec": {"type": "NodePort"}}'

kubectl patch svc nginx \
  --patch='{"spec": {"ports": [{"nodePort": 30080, "port": 80}]}}'
```

create a deployment and service:
```bash
kubectl create deployment nginx --image=nginx:alpine
kubectl expose deployment nginx --port=80 --name=nginx
```

delete deployment and service:
```bash
kubectl delete deploy/nginx svc/nginx ing/nginx
```

Ingress value for nginx
```bash
kubectl apply -f - << EOF
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: nginx
spec:
  tls:
    - hosts:
      - nginx.k8s.shubhamtatvamasi.com
      secretName: letsencrypt
  rules:
    - host: nginx.k8s.shubhamtatvamasi.com
      http:
        paths:
        - path: /
          backend:
            serviceName: nginx
            servicePort: 80
EOF
```
