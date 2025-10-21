---
sr-due: 2026-01-26
sr-interval: 97
sr-ease: 230
---

#sr-due 
`if:` — условный запуск job'а или step'а
jobs:
  deploy:
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    runs-on: ubuntu-latest
    steps:
      - run: ./deploy.sh
Job выполняется только:
- при push в `main`

`if:` в step'ах:
steps:
  - run: echo "running"
    if: env.ENVIRONMENT == 'production'
Step выполнится только если `$ENVIRONMENT == production`


[[if]]
[[GitHub Actions]]