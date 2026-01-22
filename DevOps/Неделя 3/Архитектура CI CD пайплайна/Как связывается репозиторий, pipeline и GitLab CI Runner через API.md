---
created: 2026-01-17 09:21
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-07-16
sr-interval: 180
sr-ease: 208
---
### 💡 The What
*Что это?*
Существует определенная цепочка, как Job доставляет на Runner и начинает там выполняться.

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
1. GitLab CI Server (Rails backend)
	- следит за событиями
	- запускает pipeline
	- кидает job в Redis
2. [[GitLab Runner]]:
	- раз в X секунд делает `POST /api/v4/jobs/request`
	- если его tag свопадает - GitLab отдаёт ему [[jobs]]
	- runner скачивает код (GIT_CLONE_PATH)
	- запускает `job` согласно `executor` (shell, [[Docker]], [[Kubernetes]])
	- после выполнения job выполняет `POST /api/v4/jobs:id/trace`, тем самым отсылая логи
	- и `POST /api/v4/jobs/:id` -> завершает job (передаёт состояние success/failure)
	
📦 Runner — **полностью отдельное приложение**, взаимодействующее с GitLab через [[HTTP]] API (или [[TLS]]/[[HTTPS]]).

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[GitLab CI CD]]
- **Влияет на**: [[jobs]]
- **Инсайт**: 
