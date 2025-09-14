---
sr-due: 2025-09-23
sr-interval: 12
sr-ease: 210
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