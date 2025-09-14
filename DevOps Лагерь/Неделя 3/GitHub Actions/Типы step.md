---
sr-due: 2025-10-12
sr-interval: 37
sr-ease: 230
---

#sr-due 
run: 
- name: Build
  run: go build ./...
 Запускает shell-команду (bash в Ubuntu, PowerShell в Windows)
 По умолчанию `set -e` → job упадёт при ошибке

uses - использовать готовый action:
- uses: actions/setup-node@v4
  with:
    node-version: 20
 Подключает внешний action из GitHub Marketplace
 Можно использовать:
     Официальные (`actions/*`)
     Сторонние (`org/repo@version`)
     Свои (`./.github/actions/my-action`)

комбинированные run: + uses:
- uses: actions/checkout@v4
- run: go mod tidy
- uses: actions/setup-go@v5
- run: go build ./...
📌 GitHub Actions — это **очерёдность** step’ов. В каждом job ты можешь комбинировать вызовы `uses:` и `run:`.

Пример full job для Go CLI проекта:
jobs:
  build:
    runs-on: ubuntu-latest
    env:
      CGO_ENABLED: 0
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-go@v5
        with:
          go-version: 1.22
      - name: Build
        run: go build -o bin/bigscanner ./cmd/bigscanner
      - name: Upload binary
        uses: actions/upload-artifact@v4
        with:
          name: bigscanner
          path: bin/bigscanner
📌 Это:
- Клонирует репозиторий
- Устанавливает Go
- Собирает бинарник
- Загружает артефакт (доступен в UI)

## ⚠️ Особенности:

- Каждый `job` запускается **в отдельной VM**.
- `steps` — не изолированы, **делят FS**, но **переменные не передаются** между job’ами.
- Если step возвращает ненулевой `exit code` — job падает.
- Можно использовать `continue-on-error: true` в step’е.
[[Типы step]]
[[GitHub Actions]]