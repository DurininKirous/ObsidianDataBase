---
sr-due: 2025-08-22
sr-interval: 23
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