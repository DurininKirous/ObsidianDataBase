---
sr-due: 2025-11-25
sr-interval: 36
sr-ease: 210
---

#sr-due 
Задача
Pod’ы часто используют **Persistent Volumes (PV/PVC)**, `hostPath`, `emptyDir` и другие тома.  
kubelet должен смонтировать и подать в контейнер нужный volume.  
Но у каждого стораджа (EBS, Ceph, NFS, GCE PD и т.д.) своя логика → нужна абстракция.

## CSI — что это
**CSI (Container Storage Interface)** = стандартный gRPC API, через который kubelet общается со storage-плагинами.
- kubelet не знает, какой сторадж (AWS EBS, Ceph, vSphere).
- Он всегда вызывает CSI драйвер через единый API.
- Драйвер выполняет операции монтирования/демонтирования.
[[CSI]]
[[kubelet]]