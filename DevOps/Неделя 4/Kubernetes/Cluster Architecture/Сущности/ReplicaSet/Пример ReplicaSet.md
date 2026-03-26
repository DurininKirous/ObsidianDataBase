---
sr-due: 2026-10-28
sr-interval: 225
sr-ease: 230
---

#sr-due 
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.27
        ports:
        - containerPort: 80

[[Пример ReplicaSet]]
[[ReplicaSet]]