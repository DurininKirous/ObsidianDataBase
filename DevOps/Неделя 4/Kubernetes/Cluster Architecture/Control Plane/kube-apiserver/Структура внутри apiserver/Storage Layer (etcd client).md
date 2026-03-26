---
sr-due: 2026-05-23
sr-interval: 71
sr-ease: 186
---

#sr-due 
Обеспечивает запись и чтение в etcd.
Каждый ресурс (например `Pod`, `Deployment`) имеет `StorageInterface`, который знает:
- как сериализовать объект (JSON → protobuf)
- где хранить (`/registry/pods/namespace/name`)
- как обновлять версии (`resourceVersion`)
- как обрабатывать `ListOptions` и `WatchOptions`
Используется **etcd v3 API** (`etcd/clientv3`) через `k8s.io/apiserver/pkg/storage/etcd3`
Как:
- Преобразует ресурсы в ключи:
	/registry/pods/default/nginx
	/registry/nodes/node-1
- Обновляет `resourceVersion`
- Использует lease / TTL
- Поддерживает CAS (compare-and-swap) операции
Без него:
- Состояние кластера не сохраняется
- Все ресурсы — временные, как в RAM

[[Storage Layer (etcd client)]]
[[Структура внутри apiserver]]