---
sr-due: 2026-03-03
sr-interval: 89
sr-ease: 230
---

#sr-due 
### Зачем нужен
- **Без StorageClass**: нужно руками создавать PV (например, на 10Gi), а потом писать PVC, чтобы к нему привязаться. Это статическая модель, неудобная в проде.
- **Со StorageClass**: PVC автоматически вызывает **динамическое создание PV** через CSI-драйвер (например, AWS EBS, GCP PD, Ceph, NFS).

- **provisioner** — драйвер, который создаёт реальный том. Например:
    - `kubernetes.io/aws-ebs` (устаревающий in-tree драйвер),
    - `ebs.csi.aws.com` (новый CSI).
- **parameters** — параметры тома (например, тип диска, класс скорости: `gp2`, `ssd`).
- **reclaimPolicy** — что делать с томом после удаления PVC (`Retain` / `Delete`).
- **volumeBindingMode**:
    - `Immediate` (дефолт) → PV создаётся сразу при создании PVC.
    - `WaitForFirstConsumer` → PV создаётся только когда Pod, который использует PVC, назначен на ноду (важно для облачных зон).
[[StorageClass]]
[[Volumes and Storage]]