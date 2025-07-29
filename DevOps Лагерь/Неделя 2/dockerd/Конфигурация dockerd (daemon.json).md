---
sr-due: 2025-07-30
sr-interval: 9
sr-ease: 250
---

#sr-due 

Пример:
{
  "data-root": "/var/lib/docker",
  "log-driver": "json-file",
  "storage-driver": "overlay2",
  "default-runtime": "runc",
  "insecure-registries": ["localhost:5000"]
}
Может настраивать:
- хранилище (overlay2, aufs, btrfs, zfs)
- лог-драйвер
- runtime'ы
- volume-драйверы
- параметры безопасности

[[Конфигурация dockerd (daemon.json)]]
[[dockerd]]