---
sr-due: 2025-10-17
sr-interval: 38
sr-ease: 210
---

#sr-due 
include:
  - local: '.gitlab/ci/build.yml'
  - template: 'Security/SAST.gitlab-ci.yml'
  - remote: 'https://example.com/ci.yml'
Позволяет:
- разбить CI на много yaml файлов
- подключать shared пайплайны (например, Open Source или шаблоны GitLab)
- удобно использовать шаблоны внутри монорепы

Часто используется:
.gitlab/ci/
  ├── build.yml
  ├── test.yml
  ├── deploy.yml
.gitlab-ci.yml → include их всех

include:
  - local: '.gitlab/ci/build.yml'
  - template: 'Security/SAST.gitlab-ci.yml'
  - remote: 'https://example.com/ci.yml'

[[include]]
[[gitlab-ci.yml]]