---
sr-due: 2025-09-25
sr-interval: 16
sr-ease: 230
---

#sr-due 
`needs:` — построение DAG (job зависит от других)
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: go build -o app

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - run: ./app --test
`test` job будет ждать завершения `build`.


[[needs]]
[[GitHub Actions]]