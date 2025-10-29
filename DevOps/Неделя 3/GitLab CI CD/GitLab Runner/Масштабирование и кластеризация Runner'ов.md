---
sr-due: 2025-12-27
sr-interval: 74
sr-ease: 210
---

#sr-due 
#### Подходы:
- **Self-hosted pool**: несколько shell/docker раннеров на одной машине;
- **Docker Machine**: динамически запускает/удаляет VM для CI;
- **Kubernetes executor**: автоматическое масштабирование в кластере.

📌 GitLab поддерживает:
- авто-ротацию Runner'ов;
- изолированные environments;
- groups/project runners;
- auto-scaling via `docker-machine`, `k8s`.
[[Масштабирование и кластеризация Runner'ов]]
[[GitLab Runner]]
