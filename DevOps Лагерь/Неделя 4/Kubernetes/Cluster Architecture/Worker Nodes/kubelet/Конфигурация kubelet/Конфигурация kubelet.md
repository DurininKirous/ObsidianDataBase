---
sr-due: 2025-09-30
sr-interval: 9
sr-ease: 250
---

#sr-due 
## Способы конфигурации
- **Флаги командной строки** (например, `--pod-manifest-path`, `--kubeconfig`, `--cgroup-driver`).
- **Kubelet config file** (yaml), включается флагом `--config=/var/lib/kubelet/config.yaml`.
- **Dynamic Kubelet Configuration** (через ConfigMap) — раньше был, но **deprecated**.

На проде обычно используют config-файл + systemd unit.
[[Конфигурация kubelet]]
[[kubelet]]