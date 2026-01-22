---
created: 2026-01-09 13:34
tags:
  - status/seed
  - type/concept
  - domain/cicd
  - sr-due
sr-due: 2026-07-31
sr-interval: 203
sr-ease: 230
---
### 💡 The What
*Что это?*
Все job's в GitHub Actions придерживаются определённой анатомии

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Структура одного job'а ([[jobs]]):
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
- Каждый job - отдельный процесс в изолированном  [[runner]]'е
build:
- Имя job'а
- Используется в DAG ([[Как GitLab превращает .gitlab-ci.yml в DAG-пайплайн]]), в [[needs]]:, в UI и в логах
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

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[GitHub Actions]]
- **Влияет на**: [[jobs]]
- **Инсайт**: 
