---
sr-due: 2025-10-21
sr-interval: 12
sr-ease: 210
---

#sr-due 
### PVC
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: data-pvc
  namespace: app
spec:
  accessModes: [ ReadWriteOnce ]
  resources:
    requests:
      storage: 10Gi
  storageClassName: ""   # для статического PV (или опустите для дефолтного класса)

---
### Статический PV (пример NFS или локального пути)
apiVersion: v1
kind: PersistentVolume
metadata:
  name: data-pv
spec:
  capacity:
    storage: 10Gi
  accessModes: [ ReadWriteOnce ]
  persistentVolumeReclaimPolicy: Retain
  storageClassName: ""   # должен совпадать с PVC (или оба пустые)
  nfs:                   # или другой бекенд
    server: 10.0.0.5
    path: /exports/app-data

---
### Pod, который монтирует PVC
apiVersion: v1
kind: Pod
metadata:
  name: app
  namespace: app
spec:
  containers:
  - name: web
    image: nginx:1.27
    volumeMounts:
    - name: data
      mountPath: /var/lib/app
  volumes:
  - name: data
    persistentVolumeClaim:
      claimName: data-pvc

[[Использование PVC внутри Pod]]
[[PV & PVC]]