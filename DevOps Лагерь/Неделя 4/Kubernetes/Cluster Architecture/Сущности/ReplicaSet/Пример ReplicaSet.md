---
sr-due: 2025-10-26
sr-interval: 17
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