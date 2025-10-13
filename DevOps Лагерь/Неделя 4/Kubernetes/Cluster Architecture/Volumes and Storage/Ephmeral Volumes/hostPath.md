---
sr-due: 2025-10-27
sr-interval: 18
sr-ease: 230
---

#sr-due 
- Монтирует реальный каталог/файл с хоста в Pod
- Данные живут на ноде, не исчезают при удалении Pod
- Опасность: нарушает изоляцию -> Pod может получить root-доступ к системе
Пример:
apiVersion: v1
kind: Pod
metadata:
  name: busybox-hostpath
spec:
  containers:
  - name: logger
    image: busybox
    command: ["sh", "-c", "echo 'log' >> /var/log/test.log; sleep 3600"]
    volumeMounts:
    - name: logs
      mountPath: /var/log
  volumes:
  - name: logs
    hostPath:
      path: /var/log
      type: Directory
Использование: отладка, мониторинг логов. В проде почти всегда заменяется на PVC
[[hostPath]]
[[Ephmeral Volumes]]