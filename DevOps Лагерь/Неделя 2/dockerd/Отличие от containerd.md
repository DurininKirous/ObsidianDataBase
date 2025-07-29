---
sr-due: 2025-08-01
sr-interval: 11
sr-ease: 250
---

#sr-due 

| Характеристика     | `dockerd`                  | `containerd`            |
| ------------------ | -------------------------- | ----------------------- |
| API                | HTTP REST                  | gRPC                    |
| CLI                | `docker`                   | `ctr` (вспомогательный) |
| Поддержка build    | Да (`docker build`)        | Нет                     |
| Логи               | Да (log-драйверы)          | Только stdout/stderr    |
| Сеть               | Да (bridge, overlay, host) | Нет                     |
| Volume, плагины    | Да                         | Нет                     |
| Используется в K8s | Нет                        | Да (через CRI)          |
[[Отличие от containerd]]
[[dockerd]]