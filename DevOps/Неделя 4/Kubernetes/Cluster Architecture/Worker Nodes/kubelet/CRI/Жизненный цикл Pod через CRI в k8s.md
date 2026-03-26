---
created: 2026-02-01 11:01
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-04-27
sr-interval: 57
sr-ease: 246
---
### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
1. Создание Pod
	1. kubelet вызывает RunPodSandbox:
		1. создаётся pause-контейнер (infra) [[Зачем нужен pause-контейнер]]
		2. поднимается netns, hostname, cgroup, DNS, IP через CNI
	2. Это оболочка Pod'а
2. Запуск контейнеров
	1. kubelet вызывает CreateContainer (для каждого контейнера в PodSpec)
	2. Потом StartContainer
	3. Внутри [[containerd]] это идёт через containerd-shim -> [[runc]] -> [[Cgroups]]/[[Namespaces]]
3. Поддержка
	1. kubelet через [[PLEG (Pod Lifecycle Event Generator) в k8s]] следит за ContainerStatus/PodSandboxStatus
	2. [[Probe]] (liveness/readiness/startup) выполняются через probe manager
4. Удаление Pod
	1. kubelet вызывает StopPodSandbox 
	2. Потом RemovePodSandbox

---
### 🔗 Connections
- **Родитель**: [[CRI]], [[Жизненный цикл Pod через CRI в k8s]]
- **Влияет на**: [[Нормальная жизнь]]
