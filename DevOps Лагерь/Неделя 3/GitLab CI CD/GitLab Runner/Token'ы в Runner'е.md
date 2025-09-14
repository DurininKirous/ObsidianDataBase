---
sr-due: 2025-10-23
sr-interval: 44
sr-ease: 230
---

#sr-due 

| Тип токена           | Где используется         | Назначение                           |
| -------------------- | ------------------------ | ------------------------------------ |
| `registration_token` | `gitlab-runner register` | Зарегистрировать раннер              |
| `runner token`       | в `config.toml`          | Аутентифицировать раннер             |
| `CI_JOB_TOKEN`       | в job внутри CI          | Доступ к API / Registry / артефактам |
| `CI_REGISTRY_TOKEN`  | Docker registry auth     | Пуш/пул образов                      |
[[Token'ы в Runner'е]]
[[GitLab Runner]]