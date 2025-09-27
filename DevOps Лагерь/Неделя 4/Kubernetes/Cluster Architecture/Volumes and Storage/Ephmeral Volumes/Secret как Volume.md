- Secret хранит чувствительные данные
- Можно смонтировать как файлы или переменные окружения
Пример:
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
type: Opaque
data:
  username: YWRtaW4=   # base64(admin)
  password: c2VjcmV0   # base64(secret)
---
apiVersion: v1
kind: Pod
metadata:
  name: app-pod
spec:
  containers:
  - name: app
    image: busybox
    command: ["sh", "-c", "cat /secrets/username; sleep 3600"]
    volumeMounts:
    - name: secret-volume
      mountPath: /secrets
  volumes:
  - name: secret-volume
    secret:
      secretName: db-secret
