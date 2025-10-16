---
sr-due: 2026-01-09
sr-interval: 87
sr-ease: 230
---

#sr-due 
Структура одного job'а:
jobs:
  build:
    runs-on: ubuntu-latest
    env:
      GOFLAGS: -mod=readonly
    steps:
      - uses: actions/checkout@v4
      - name: Setup Go
        uses: actions/setup-go@v5
        with:
          go-version: 1.22
      - name: Build project
        run: go build -v ./cmd/...

Пояснение по каждому полю:
jobs: 
- Главный уровень в workflow'е после on:
- Каждый job - отдельный процесс в изолированном runner'е
build:
- Имя job'а
- Используется в DAG, в needs:, в UI и в логах
runs-on: 
- Указывает, на какой машине будет выполняться job
- Возможные значения:
	- `ubuntu-latest`, `ubuntu-22.04`, `windows-latest`, `macos-latest`
	- `self-hosted` — если у тебя собственный runner
env:
- Объявлет переменные окружения на уровне job'ов
- Они доступны в run: и в action'ах
- Можно переопределять локально в step'е
```
env:
  NODE_ENV: production
```

steps:
- Список **действий внутри job**, выполняются **строго по порядку**.
[[Анатомия job'а]]
[[GitHub Actions]]