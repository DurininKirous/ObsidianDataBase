---
sr-due: 2026-03-20
sr-interval: 140
sr-ease: 250
---

#sr-due 
Pipeline
│
├── Stage: build
│   ├── Job: fetch code
│   └── Job: compile, build binary
│
├── Stage: test
│   ├── Job: run unit tests
│   └── Job: run integration tests
│
├── Stage: package
│   └── Job: generate artifacts (docker, tar, wheel)
│
├── Stage: deploy
│   └── Job: deploy to staging
│
└── Stage: cleanup / notify

---

Особенности:
- Jobs внутри stage - выполняются параллельно
- Stages - строго по порядку
- Job может зависеть от другого job через `needs` или `dependencies`
- Каждая job может передавать данные (через artifacts) или кэшировать (через cache)
[[CI CD Pipeline Логическая модель]]
[[Архитектура CI CD пайплайна]]