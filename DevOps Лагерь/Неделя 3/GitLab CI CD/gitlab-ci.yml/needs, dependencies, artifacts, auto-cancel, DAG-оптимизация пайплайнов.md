---
sr-due: 2025-10-08
sr-interval: 30
sr-ease: 210
---

#sr-due 
`artifacts:` — передача артефактов между job’ами
build:
  script:
    - go build -o app
  artifacts:
    paths:
      - путь/к/файлу_или_папке
	  
📌 Артефакты:
- сохраняются после job;
- могут быть получены в другой job через `dependencies` или `needs`;
- доступны в UI для скачивания;
- не живут между pipeline'ами (в отличие от `cache:`).

`dependencies:` — "получить артефакты от job"
test:
  dependencies:
    - build
  script:
    - ./app --version
	
📌 Работает только между **разными `stage`**.  
GitLab возьмёт артефакты из `build` и примонтирует их в `test`.

`needs:` — **настоящая DAG-зависимость**
test:
  needs:
    - job: build
  script:
    - ./app --test
📌 Позволяет:
- запустить `test` сразу после `build`, **не дожидаясь всей `stage: build`**;
- **ускоряет пайплайн**, особенно если в `build` много job'ов, а `test` зависит только от одного.

> ⚠️ `needs:` включает передачу `artifacts` **автоматически**, как `dependencies`.

Auto-cancel pipelines (оптимизация)
workflow:
  rules:
    - when: always

  # авто-отмена предыдущих, если pipeline ещё не запущен
  # и пришёл новый коммит в ту же ветку
  auto_cancel: true
📌 Особенно важно на `feature`-ветках и `main`, чтобы не грузить CI на каждый пуш.


[[needs, dependencies, artifacts, auto-cancel, DAG-оптимизация пайплайнов]]
[[gitlab-ci.yml]]