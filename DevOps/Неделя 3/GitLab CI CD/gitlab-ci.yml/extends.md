---
sr-due: 2026-08-27
sr-interval: 231
sr-ease: 250
---

#sr-due 
.default-job-template:
  before_script:
    - echo preparing
  script:
    - echo doing work
  after_script:
    - echo cleaning

build:
  extends: .default-job-template
  script:
    - echo building

Позволяет:
- не дублировать before_script, image, artifacts
- создавать набор настроек для reuse
[[extends]]
[[gitlab-ci.yml]]