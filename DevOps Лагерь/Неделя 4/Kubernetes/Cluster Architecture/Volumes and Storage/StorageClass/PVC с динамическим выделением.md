---
sr-due: 2025-11-18
sr-interval: 28
sr-ease: 228
---

#sr-due 
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-dynamic
  namespace: app
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 20Gi
  storageClassName: gp2
```
Когда создаёшь этот PVC, Kubernetes **сам создаст PV** через StorageClass `gp2` → и свяжет PVC ↔ PV.
[[PVC с динамическим выделением]]
[[StorageClass]]