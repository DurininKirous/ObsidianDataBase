---
sr-due: 2025-10-20
sr-interval: 45
sr-ease: 250
---

#sr-due 
Это специальные зарезервированные job'ы, которые не выполняются как обычные, но могут быть подключены автоматически в extends, работают только в связке с extends.

.pre - выполняется до всех job'ов
.pre:
  before_script:
    - echo "🧼 pre stage setup"

.post - выполняется после всех job'ов
.post:
  after_script:
    - echo "🧹 cleaning up"

.default - шаблон значений для всех job'ов, если они не переопределены
.default:
  image: golang:1.22
  before_script:
    - echo "Default setup"

GitLab **автоматически применяет `extends: [.default, .pre, .post]`** ко всем job’ам, если они не указали `extends:` явно.
[[pre, .post, .default, .extends]]
[[gitlab-ci.yml]]