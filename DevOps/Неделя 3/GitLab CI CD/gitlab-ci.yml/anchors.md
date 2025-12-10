---
sr-due: 2026-04-16
sr-interval: 128
sr-ease: 210
---

#sr-due 
.reusable-steps: &steps
  script:
    - echo "doing stuff"
    - echo "done"

job1:
  <<: *steps

job2:
  <<: *steps
  script:
    - echo "overridden"

Позволяет **вставлять YAML блоки по ссылке**. Работает до GitLab — это YAML-фича.
[[anchors]]
[[gitlab-ci.yml]]