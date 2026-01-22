---
created: 2026-01-17 10:39
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-06-26
sr-interval: 160
sr-ease: 230
---
### 💡 The What
*Что это?*
**Static Pod** — это Pod, который запускает **kubelet напрямую с диска ноды**, минуя создание Pod в API.

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- Манифест лежит локально (часто: `/etc/kubernetes/manifests/…`).
- [[kubelet]] сам читает файл, валидирует, **создаёт/перезапускает/удаляет** контейнеры.
- Никакого участия [[kube-scheduler]]: [[Pod]] **жёстко привязан** к этой ноде.
Зачем:
- **Бустрэп/контроль-плейн**: даже если [[kube-apiserver]] недоступен, kubelet поднимет `kube-apiserver`, `kube-scheduler`, `kube-controller-manager`, `etcd`.
- Критичные локальные агенты, где нужна независимость от control plane.
Включение:
- Флаг kubelet: `--pod-manifest-path=/etc/kubernetes/manifests` (или `--manifest-url`).
- Kubelet **следит за каталогом** (file watcher): создание/изменение/удаление файла → reconcile.

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[kubelet]]
- **Влияет на**: [[...]]
- **Инсайт**: 
