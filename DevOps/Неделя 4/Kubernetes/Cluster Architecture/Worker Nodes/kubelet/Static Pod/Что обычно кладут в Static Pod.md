---
sr-due: 2026-01-19
sr-interval: 71
sr-ease: 230
---

#sr-due 
- Компоненты control plane (kubeadm так и делает):  
    `kube-apiserver`, `kube-controller-manager`, `kube-scheduler`, `etcd`.
- Томá обычно `hostPath` (сертификаты, конфиги, сокеты), чтобы процесс видел файловую систему ноды.
[[Что обычно кладут в Static Pod]]
[[Static Pod в K8S]]