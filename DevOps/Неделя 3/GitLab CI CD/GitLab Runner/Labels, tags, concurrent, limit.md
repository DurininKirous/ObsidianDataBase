---
sr-due: 2027-02-17
sr-interval: 338
sr-ease: 250
---

#sr-due 
`tags` в `.gitlab-ci.yml`:
build:
  tags:
    - docker
    - go
>Job получит только тот Runner, у которого в `config.toml` есть соответствующие `tags`.

`concurrent` (в глобальном Runner config)
`concurrent = 4  # максимум одновременных job`

`limit` (на уровне Runner)
[runners]
  limit = 2  # максимум job одновременно на этом раннере

[[Labels, tags, concurrent, limit]]
[[GitLab Runner]]