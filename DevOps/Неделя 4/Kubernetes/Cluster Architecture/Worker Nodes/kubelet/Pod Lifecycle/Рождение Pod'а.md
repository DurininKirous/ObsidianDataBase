---
sr-due: 2026-02-20
sr-interval: 83
sr-ease: 210
---

#sr-due 
События:
1. Создание Pod в API -> phase=Pending, condition PodScheduled=False (reason=Unchedulable) до назначения
2. Scheduler выбирает ноду -> PodScheduled=True, в spec.nodeName появляется нода
3. kubelet подхватывает Pod и запускается SyncPod:
	1. Volumes/CSI: подготавливает и монтирует тома, подсовывает Secret/ConfigMap
	2. Pod Sandbox: создаёт pause-контейнер + netns + CNI ADD (IP, routes, DNS) 
	3. Init Containers: выполняются последовательно до успеха каждого
	4. App containers: pull -> create -> start. Старт не равен "готов к трафику"
Типичные статусы/причины на старте:
- Pending + Unschedulable (нет ресурсов/taints/affinity не сошлись)
- ContainerCreating (монтирование томов/CNI/создание sandbox)
- ErrImagePull / ImagePullBackOff (нет доступа / не найден образ)
- CreateContainerConfigError (ошибка в манифесте: envFrom, volumeMount и т.д.)
[[Рождение Pod'а]]
[[Pod Lifecycle]]