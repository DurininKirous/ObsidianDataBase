---
sr-due: 2025-11-10
sr-interval: 32
sr-ease: 230
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