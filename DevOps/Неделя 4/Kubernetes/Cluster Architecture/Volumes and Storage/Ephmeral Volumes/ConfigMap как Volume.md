---
created: 2026-01-05 20:47
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-04-18
sr-interval: 103
sr-ease: 43
---
### 💡 The What
*Что это?*
ConfigMap можно использовать как Volume в Kubernetes

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- ConfigMap хранит конфигурационные файлы
- Можно примонтировать ConfigMap как файлы в Pod
- Изменения в ConfigMap автоматически подтянутся в Pod (с небольшой задержкой), если файл не был изменён самим приложением
Пример:
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  config.yaml: |
    port: 8080
    debug: true
---
apiVersion: v1
kind: Pod
metadata:
  name: app-pod
spec:
  containers:
  - name: app
    image: busybox
    command: ["sh", "-c", "cat /config/config.yaml; sleep 3600"]
    volumeMounts:
    - name: config-volume
      mountPath: /config
  volumes:
  - name: config-volume
    configMap:
      name: app-config
```
---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[hostPath]]**: Небезопасен, доступ к системе
- VS [[EmptyDir]]: Не переиспользуем, очищается при завершении пода


---
### 🔗 Connections
- **Родитель**: [[Ephmeral Volumes]]
- **Влияет на**: [[...]]
- **Инсайт**: 
