---
created: 2026-01-18 08:27
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-07-01
sr-interval: 164
sr-ease: 230
---
### 💡 The What
*Что это?*
Каждый из типов Probe имеет свою семантику

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
### readinessProbe
- Успех -> Pod попадает в Endpoints сервиса
- Провал -> Pod исключается из Endpoints 
- Не рестартит контейнер
- Ставится/снимается `PodCondition Ready`

### livenessProbe
- Провал подряд `failureThreshold` раз -> kubelet шлёт SIGKILL контейнеру (restarts), затем обычная перезапуск-логика и бэкофф
- На трафик напрямую не влияет 

### startupProbe
- Пока startup не стала `Success`, и liveness, и readinessне выполняются
- Если startup провалена `failureThreshold` раз -> контейнер убивается (как liveness)
- Используй для тяжёлого старта - чтобы liveness не убивал раньше времени

---
### 🔗 Connections
- **Родитель**: [[Probe]]
- **Влияет на**: [[Probes и готовность]]
- **Инсайт**: 
