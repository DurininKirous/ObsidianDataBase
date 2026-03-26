---
created: 2026-01-28 17:53
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-07-02
sr-interval: 155
sr-ease: 210
---
### 💡 The What
*Что это?*
Finalizers имеют широкое применение в кластере, в том числе с коробки

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- [[PV & PVC]]-protection: kubernetes.io/pvc-protection, kubernetes.io/pv-protection - не дают удалить ресурс, пока это может нарушить целостность
- Namespace deletion: у Namespace есть финалайзер (обычно `kubernetes`), пока контроллер не подчистит все ресурсы внутри - неймспейс висит в Terminating [[Namespace Controller]]
- Foreground deletion GC: при прямом удалении владельца с политикой `Foreground` GC добавляет финалайзер к `owner`, чтобы дождаться удаления зависимых

---
### 🔗 Connections
- **Родитель**: [[Finalizers]]
