---
sr-due: 2025-11-01
sr-interval: 37
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