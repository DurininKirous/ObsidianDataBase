---
sr-due: 2025-10-25
sr-interval: 16
sr-ease: 230
---

#sr-due 
- Самый базовый ephmeral том
- Создаётся пустой каталог на ноде, когда Pod запускается
- Доступен всем контейнерам внутри Pod
- Удаляется вместе с Pod
Применения:
- кеши, временные файлы, scratch space, шаринг файлов между контейнерами
Пример:
apiVersion: v1
kind: Pod
metadata:
  name: busybox-emptydir
spec:
  containers:
  - name: writer
    image: busybox
    command: ["sh", "-c", "echo hello > /data/hello; sleep 3600"]
    volumeMounts:
    - name: cache
      mountPath: /data
  - name: reader
    image: busybox
    command: ["sh", "-c", "cat /data/hello; sleep 3600"]
    volumeMounts:
    - name: cache
      mountPath: /data
  volumes:
  - name: cache
    emptyDir: {}
Особенности:
- Можно указать `medium: Memory` -> хранить в tmpfs
- Подходит для "внутриподовых" сценариев
[[EmptyDir]]
[[Ephmeral Volumes]]