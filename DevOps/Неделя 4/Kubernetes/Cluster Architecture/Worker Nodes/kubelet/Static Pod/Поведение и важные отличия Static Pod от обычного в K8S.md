---
created: 2026-01-17 09:45
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-06-25
sr-interval: 159
sr-ease: 230
---
### 💡 The What
*Что это?*
Static Pod отличается от обычного пода в своем поведении, во взаимодействии с ним 

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
**1) Обновление**
- Меняешь локальный YAML → [[kubelet]] замечает изменение → **пересоздаёт** static pod (graceful: SIGTERM → `terminationGracePeriodSeconds` → SIGKILL).
- Mirror в API обновится вслед за реальным подом. Никакого rolling update — это **жизнь одного пода** на одной ноде.

**2) Удаление**
- `kubectl delete pod …` удалит **только mirror**, **контейнеры продолжат работать**.  
    Через мгновение kubelet снова создаст mirror.  
    👉 Чтобы реально удалить — **удали/переименуй файл** манифеста на ноде.

**3) Отказ API-сервера**
- Static pod **запустится и без API**, mirror появится, когда API поднимется.  
    Это ключ к «самовосстановлению» control plane.

**4) Сервисы и [[Endpoint]]**
- Как только mirror существует и Pod имеет `Ready=True`, сервис с подходящим `selector` **включит его в Endpoints**.  
    (Без mirror API просто не знает, что под существует.)

**5) Безопасность/квоты/адмиссия**

- Static pod создаётся **в обход** обычной цепочки admission в API (он не «приходит» через [[kube-apiserver]]).
- ResourceQuota/LimitRange его **не блокируют на входе** (они работают на admission).  
    Но **[[Cgroups]]/limits из PodSpec** kubelet применяет как обычно.

**6) Привязка к ноде**
- Static pod всегда на **той же ноде**, где лежит файл. Никаких перескоков по кластеру.
- `nodeName` фактически фиксирован, [[taints]]/[[Affinity and AntiAffinity]] не участвуют.

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[Kubernetes]]
- **Влияет на**: [[Control Plane]]
- **Инсайт**: Control Plane реализован через набор Static Pod'ов
