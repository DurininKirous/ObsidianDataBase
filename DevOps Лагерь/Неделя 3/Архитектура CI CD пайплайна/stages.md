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