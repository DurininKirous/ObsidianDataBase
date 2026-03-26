---
created: 2026-01-12 20:48
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-03-18
sr-interval: 17
sr-ease: 224
---
### 💡 The What
*Что это?*
Провайдер - отдельная программа (бинарник вроде terraform-provider-yandex), которая знает специфику API (Yandex, AWS).

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- [[Core модуль в Terraform]] запускает её как дочерний процесс, с помощью него Terraform понимает, как производить стандартные для него операции типо планирования или изменения ресурсов.

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[...]]
- **Влияет на**: [[Plugin Protocol в Terraform]]
- **Инсайт**: 
