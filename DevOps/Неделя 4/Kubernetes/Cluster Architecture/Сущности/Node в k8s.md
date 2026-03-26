---
created: 2026-02-04 08:22
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-08-10
sr-interval: 187
sr-ease: 230
---
### 💡 The What
*Что это?*
Node - это объект, представляющий рабочую машину, на которой запускаются Pod'ы

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
У Node есть:
- status.conditions
- labels / [[Taints and Tolerations]]
- Информация о CPU/RAM/Disk/Network capacity

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[Pod]]**: Нода - место размещения подов 


---
### 🔗 Connections
- **Родитель**: [[Сущности]], [[Node в k8s]]
