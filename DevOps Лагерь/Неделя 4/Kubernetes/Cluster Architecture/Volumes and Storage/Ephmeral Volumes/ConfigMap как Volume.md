---
sr-due: 2025-09-27
sr-interval: 1
sr-ease: 230
---

#sr-due 
- ConfigMap хранит конфигурационные файлы
- Можно примонтировать ConfigMap как файлы в Pod
Пример:
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
Изменения в ConfigMap автоматически подтянутся в Pod (с небольшой задержкой), если файл не был изменён самим приложением.
[[ConfigMap как Volume]]
[[Ephmeral Volumes]]