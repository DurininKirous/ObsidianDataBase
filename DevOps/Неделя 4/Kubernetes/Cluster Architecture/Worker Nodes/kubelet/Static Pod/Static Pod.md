---
sr-due: 2025-11-08
sr-interval: 30
sr-ease: 230
---

#sr-due 
**Static Pod** — это Pod, который запускает **kubelet напрямую с диска ноды**, минуя создание Pod в API.
- Манифест лежит локально (часто: `/etc/kubernetes/manifests/…`).
- kubelet сам читает файл, валидирует, **создаёт/перезапускает/удаляет** контейнеры.
- Никакого участия scheduler: Pod **жёстко привязан** к этой ноде.
Зачем:
- **Бустрэп/контроль-плейн**: даже если API-сервер недоступен, kubelet поднимет `kube-apiserver`, `kube-scheduler`, `kube-controller-manager`, `etcd`.
- Критичные локальные агенты, где нужна независимость от control plane.
Включение:
- Флаг kubelet: `--pod-manifest-path=/etc/kubernetes/manifests` (или `--manifest-url`).
- Kubelet **следит за каталогом** (file watcher): создание/изменение/удаление файла → reconcile.
[[Static Pod]]
[[kubelet]]