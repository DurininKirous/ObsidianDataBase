---
sr-due: 2025-10-17
sr-interval: 19
sr-ease: 206
---

#sr-due 
Позволяет контроллерам, kubelet и другим клиентам **следить за изменениями** в API.
Клиенты (scheduler, controller, kubelet, `kubectl get -w`) подписываются на `watch`.
- Каждый `watch` обрабатывается через `WatchCache`, чтобы не дёргать постоянно etcd
- `resourceVersion` позволяет продолжить после reconnect
- Используется `gochannel` → multiplex → broadcast
Работает через long-polling HTTP:
	GET /api/v1/pods?watch=true&resourceVersion=1234
Как:
- Поддерживает подключение клиентов с флагом `?watch=true`
- Каждому клиенту — свой канал
- Использует внутренний watch cache для ускорения
Без него:
- controller-manager, scheduler, kubelet не смогут реагировать на изменения
- кластер не будет работать как event-driven система

[[Watch Broadcasters]]
[[Структура внутри apiserver]]