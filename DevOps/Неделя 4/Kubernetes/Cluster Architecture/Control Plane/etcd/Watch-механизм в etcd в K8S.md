---
created: 2026-01-17 10:45
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-05-06
sr-interval: 109
sr-ease: 190
---
### 💡 The What
*Что это?*
etcd - один из немногих хранилищ с встроенной поддержкой watch API

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- каждый объект имеет mod_revision
- каждый клиент может открыть Watch(key, from_revision)
- используется long-lived streaming gRPC connection
[[kube-apiserver]] держит один watch, и рассылает своих клиентов (controller-manager, scheduler, etc.)

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[etcd]], [[Watch Broadcasters]]
- **Влияет на**: [[...]]
- **Инсайт**: 
