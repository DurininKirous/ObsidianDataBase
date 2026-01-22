---
created: 2026-01-05 03:35
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-05-14
sr-interval: 129
sr-ease: 230
---
### 💡 The What
*Что это?*
Это временные хранилища данных, которые создаются вместе с инициализацией Pod'а. Данные живут в слое overlayFS и исчезают при удалении Pod'а

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- Иногда нужны временные данные: кэш, буферы, обмен файлами между контейнерами
- Для этого Kubernetes даёт ephmeral volumes. Они живут только, пока живёт Pod.

### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[PV & PVC]]**: Является постоянным хранилищем данных, сохраняет их даже после удаления Pod'a, но сложнее в инициализации и неудобнее в задачах, для которых используют Ephmeral Volumes
- **Trade-off**:
	- Плюсы: Быстро управляем данными и не думаем об их очищении
	- Минусы: Пока не найдены

---
### 🔗 Connections
- **Родитель**: [[ObsidianDataBase/Linux Internals/Файловые системы/Типы файловых систем/overlayfs|overlayfs]], [[ObsidianDataBase/DevOps/Неделя 2/Linux primitives/overlayFS/overlayFS|overlayFS]], [[Связь OverlayFS с Snapshot'ами в Docker]], [[Структура overlayFS]]
- **Влияет на**: [[EmptyDir]], [[hostPath]], [[Secret как Volume]], [[ConfigMap как Volume]]
- **Инсайт**: Использовать для управления временными данными и передачей их между контейнерами
