---
sr-due: 2025-07-31
sr-interval: 1
sr-ease: 230
---

#sr-due 
> Фаза обработки. Часто: build, test, package, release, deploy
- Порядок stages строго контролирует flow
- Ставь test раньше deploy, lint раньше build, cleanup после всего

Gitlab:
```
stages:
  - lint
  - test
  - build
  - deploy
  - cleanup
```

[[stages]]
[[Архитектура CI CD пайплайна]]