---
sr-due: 2025-10-07
sr-interval: 12
sr-ease: 230
---

#sr-due 
gRPC сервис для обработки запросов к container runtime

### Зачем нужен CRI
- kubelet сам не умеет запускать контейнеры 
- Он делегирует работу container runtime 
- Чтобы kubelet не зависел от конкретного runtime, сделали стандартный API - CRI (gRPC)

### CRI = Два gRPC сервиса
1. RuntimeService (работа с контейнерам/Pod Sandbox)
	1. RunPodSandbox - создать Sandbox
	2. StopPodSandbox / RemovePodSandbox
	3. CreateContainer - создать контейнер в Pod
	4. StartContainer / StopContainer / RemoveContainer
2. ImageService (работа с образами)
	1. PullImage
	2. ImageStatus
	3. ListImage
	4. RemoveImage
[[CRI]]
[[kubelet]]