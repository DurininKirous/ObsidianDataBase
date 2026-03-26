---
sr-due: 2026-06-08
sr-interval: 84
sr-ease: 210
---

#sr-due 
1. Пользователь создаёт PVC
2. Контроллер (CSI external-provisioner) вызывает CreateVolume у CSI драйвера
3. При назначении Pod на ноду kubelet:
	1. вызывает у драйвера `NodeStageVolume` (например, примонтировать EBS к /var/lib/kubelet/plugins/kubernetes.io/csi/pv/... )
	2. затем `NodePublishVolume` — примонтировать том внутрь pod sandbox (через bind mount).
4. kubelet запускает контейнер уже с примонтированным volume.
[[Как kubelet подмонтирует PVC в Pod]]
[[CSI]]