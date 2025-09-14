---
sr-due: 2025-10-15
sr-interval: 39
sr-ease: 230
---

#sr-due 
🔑 Команда регистрации:
`sudo gitlab-runner register`

Будут вопросы:
- URL GitLab: `https://gitlab.com` или локальный;
- Token: получаешь в `Settings → CI/CD → Runners`;
- Executor: `shell`, `docker`, и т.д.;
- Tags: например `go`, `prod`, `ci` — чтобы GitLab знал, кому выдавать job.
    
После этого создаётся `config.toml`:

📄 config.toml — ключевой файл Runner'а
[[runners]]
  name = "local-shell"
  url = "https://gitlab.com"
  token = "glrt-abc123"
  executor = "shell"

  [runners.custom_build_dir]
  [runners.cache]
    [runners.cache.s3]
    [runners.cache.gcs]

[[Регистрация Runner'а и config.toml]]
[[GitLab Runner]]