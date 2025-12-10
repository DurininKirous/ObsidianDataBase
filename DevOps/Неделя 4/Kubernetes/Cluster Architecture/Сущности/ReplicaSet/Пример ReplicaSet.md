---
sr-due: 2026-03-17
sr-interval: 98
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