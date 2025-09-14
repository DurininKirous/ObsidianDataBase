---
sr-due: 2025-10-19
sr-interval: 40
sr-ease: 208
---

#sr-due 
Цепочка:
1. GitLab CI Server (Rails backend)
	- следит за событиями
	- запускает pipeline
	- кидает job в Redis
2. GitLab Runner:
	- раз в X секунд делает `POST /api/v4/jobs/request`
	- если его tag свопадает - GitLab отдаёт ему `job`
	- runner скачивает код (GIT_CLONE_PATH)
	- запускает `job` согласно `executor` (`shell`, `docker`, `k8s`)
	- после выполнения job выполняет `POST /api/v4/jobs:id/trace`, тем самым отсылая логи
	- и `POST /api/v4/jobs/:id` -> завершает job (передаёт состояние success/failure)
	
📦 Runner — **полностью отдельное приложение**, взаимодействующее с GitLab через HTTP API (или TLS/HTTPS).
[[Как связывается репозиторий, pipeline и runner через API]]
[[Архитектура CI CD пайплайна]]