---
sr-due: 2025-10-08
sr-interval: 13
sr-ease: 230
---

#sr-due 
1. Создание Pod
	1. kubelet вызывает RunPodSandbox:
		1. создаётся pause-контейнер (infra)
		2. поднимается netns, hostname, cgroup, DNS, IP через CNI
	2. Это оболочка Pod'а
2. Запуск контейнеров
	1. kubelet вызывает CreateContainer (для каждого контейнера в PodSpec)
	2. Потом StartContainer
	3. Внутри containerd это идёт через containerd-shim -> runc -> cgroup/namespaces
3. Поддержка
	1. kubelet через PLEG следит за ContainerStatus/PodSandboxStatus
	2. Пробы (liveness/readiness/startup) выполняются через probe manager
4. Удаление Pod
	1. kubelet вызывает StopPodSandbox 
	2. Потом RemovePodSandbox

[[Жизненный цикл Pod через CRI]]
[[CRI]]