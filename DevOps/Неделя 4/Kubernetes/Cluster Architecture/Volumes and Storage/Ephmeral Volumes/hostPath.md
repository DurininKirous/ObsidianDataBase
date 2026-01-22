---
created: 2026-01-07 12:07
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-05-21
sr-interval: 134
sr-ease: 230
---
### 💡 The What
*Что это?*
hostPath - одна из разновидностей Ephmeral Volumes в Kubernetes. Представляет собой вмонтированный в под каталог с хоста

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- Монтирует реальный каталог/файл с хоста в [[Pod]]
- Данные живут на ноде, не исчезают при удалении Pod
- Опасность: нарушает изоляцию -> Pod может получить root-доступ к системе
Пример:
```yaml
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
```
Использование: отладка, мониторинг логов. В проде почти всегда заменяется на PVC

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[ConfigMap как Volume]]**: Безопаснее, переиспользумее 
- **Trade-off**: 
	- Получаем быстрый доступ к данным
	- Небезопасно


---
### 🔗 Connections
- **Родитель**: [[Ephmeral Volumes]]
