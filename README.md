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

Alt command
```bash
kubectl run nginx --image=nginx:alpine --restart=Never --port=80 --expose

kubectl patch svc nginx \
  --patch='{"spec": {"type": "NodePort"}}'

kubectl patch svc nginx \
  --patch='{"spec": {"ports": [{"nodePort": 30080, "port": 80}]}}'
```
