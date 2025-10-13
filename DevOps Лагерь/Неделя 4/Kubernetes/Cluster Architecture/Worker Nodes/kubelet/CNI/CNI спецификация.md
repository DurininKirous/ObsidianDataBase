---
sr-due: 2025-11-09
sr-interval: 31
sr-ease: 230
---

#sr-due 
- Плагины - это бинарники в `/opt/cni/bin` (flannel, calico, cilium)
- Конфиги в `/etc/cni/net.d/*.conf`
- kubelet указывает путь к CNI плагинам (--cni-bin-dir, --cni-conf-dir)
kubelet не знает, какой плагин выбран. Он только вызывает CNI API (ADD/DEL)
[[CNI спецификация]]
[[CNI]]