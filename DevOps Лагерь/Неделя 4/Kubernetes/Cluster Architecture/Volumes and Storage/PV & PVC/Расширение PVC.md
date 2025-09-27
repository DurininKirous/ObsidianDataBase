#sr-due 
- Работает, если:
    - у **StorageClass** включён `allowVolumeExpansion: true`,
    - **CSI-драйвер поддерживает** resize,
    - в PVC меняете `resources.requests.storage: 10Gi → 20Gi`.
- **Filesystem resize** обычно делает kubelet при следующем монтировании (иногда «онлайн», зависит от драйвера/ФС).
- Для `volumeMode: Block` логика иная (без ФС).
[[Расширение PVC]]
[[PV & PVC]]