---
sr-due: 2026-10-11
sr-interval: 217
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
[[Пример StorageClass]]
[[StorageClass]]