---
sr-due: 2025-10-24
sr-interval: 15
sr-ease: 230
---

#sr-due 
```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: gp2
provisioner: ebs.csi.aws.com
parameters:
  type: gp2
  fsType: ext4
reclaimPolicy: Delete
volumeBindingMode: WaitForFirstConsumer
allowVolumeExpansion: true

```
Объяснение:
- `provisioner: ebs.csi.aws.com` → CSI драйвер для AWS EBS.
- `type: gp2` → стандартные SSD.
- `reclaimPolicy: Delete` → диск удалится, если PVC удалён.
- `volumeBindingMode: WaitForFirstConsumer` → дождёмся, пока Pod будет назначен на ноду в правильной зоне.
- `allowVolumeExpansion: true` → PVC можно ресайзить.
[[Пример StorageClas]]
[[StorageClass]]