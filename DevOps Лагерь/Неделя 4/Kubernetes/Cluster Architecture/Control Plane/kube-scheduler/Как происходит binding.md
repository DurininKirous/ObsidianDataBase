---
sr-due: 2025-09-14
sr-interval: 2
sr-ease: 230
---

#sr-due 
Когда Node выбрана:
1. Scheduler вызывает Bind() плагин -> отправляет PATCH
	{
	  "spec": {
	    "nodeName": "node-xyz"
	  }
	}
2. Apiserver сохраняет это в etcd
3. kubelet на `node-xyz` через `watch` замечает новый Pod с spec.nodeName = "node-xyz"
4. Запускает pod

[[Как происходит binding]]
[[kube-scheduler]]