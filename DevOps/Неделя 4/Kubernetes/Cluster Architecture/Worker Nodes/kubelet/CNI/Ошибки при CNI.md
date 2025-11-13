---
sr-due: 2026-01-15
sr-interval: 67
sr-ease: 230
---

#sr-due 
- Pod застрял в `ContainerCreating`, причина в `Events`:
    - `failed to set up pod network: CNI failed to assign IP`.
- Часто проблемы:
    - нет плагина в `/opt/cni/bin/`,
    - неверный конфиг в `/etc/cni/net.d/`,
    - IPAM (менеджер IP) не может выдать адрес.
[[Ошибки при CNI]]
[[CNI]]