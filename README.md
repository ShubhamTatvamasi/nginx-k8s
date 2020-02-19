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
```
kubectl run nginx --image=nginx:alpine --expose --port=80 --restart=Never
```
