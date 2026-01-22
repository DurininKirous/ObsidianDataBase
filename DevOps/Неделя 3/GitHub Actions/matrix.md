---
sr-due: 2026-07-26
sr-interval: 199
sr-ease: 230
---

#sr-due 
matrix - запуск job'ов с разными комбинациями
jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        go: [1.21, 1.22]
        os: [ubuntu-latest, macos-latest]
    name: Test on Go ${{ matrix.go }} / ${{ matrix.os }}
    steps:
      - uses: actions/setup-go@v5
        with:
          go-version: ${{ matrix.go }}
      - run: go test ./...

GitHub создаёт 4 job’а:
- Go 1.21 + Ubuntu
- Go 1.21 + macOS
- Go 1.22 + Ubuntu
- Go 1.22 + macOS

matrix + exclude
strategy:
  matrix:
    go: [1.21, 1.22]
    os: [ubuntu-latest, windows-latest]
    exclude:
      - go: 1.21
        os: windows-latest

Исключает нежелательные комбинации

matrix + include
include:
  - go: 1.20
    os: ubuntu-20.04

Можно добавить вручную кастомные связки
[[matrix]]
[[GitHub Actions]]