---
sr-due: 2026-06-27
sr-interval: 208
sr-ease: 250
---

#sr-due 
- dockerd предоставляет полноценный REST API
- Поддерживает JSON-интерфейс для: images, containers, networks, exec и пр.
- Пример:
	- POST /containers/create
	- POST /containers/id/start
	- GET /containers/json <- это docker ps
	- GET /images/json <- это docker images
Используется:
- docker CLI
- инструменты типо Portainer, Rancher
- CI/CD (через HTTP вызовы)
[[Docker Remote API]]
[[dockerd]]