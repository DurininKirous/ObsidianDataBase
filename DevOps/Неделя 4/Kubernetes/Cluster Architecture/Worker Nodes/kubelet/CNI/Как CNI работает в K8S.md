---
created: 2026-01-17 09:50
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-06-24
sr-interval: 158
sr-ease: 230
---
### 💡 The What
*Что это?*
Описание процесса, как CNI плагин работает в K8s

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
1. [[kubelet]] вызывает [[CRI]] -> RunPodSandbox
2. CRI (CRI-O/containerd) создаёт pause-container (netns; [[Зачем нужен pause-контейнер]])
3. CRI вызывает CNI Pluginс операцией ADD
	1. параметры: pod name, namespace, netns, требуемая сеть
	2. результат: IP-адрес, маршруты, [[ObsidianDataBase/DevOps/Неделя 1/Сети/DNS/DNS]]
4. kubelet записывает IP [[Pod]] в статус
5. При удалении Pod -> CRI вызывает `DEL` в CNI, чтобы убрать интерфейс/IP

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
