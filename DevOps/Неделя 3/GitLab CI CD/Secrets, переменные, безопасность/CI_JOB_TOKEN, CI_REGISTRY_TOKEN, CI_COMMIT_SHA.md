---
sr-due: 2026-05-03
sr-interval: 62
sr-ease: 230
---

#sr-due 
### `CI_JOB_TOKEN` — один из важнейших
- автоматом создаётся GitLab’ом;
- используется для:
    - `docker login` в GitLab Container Registry;
    - `git clone`, `pull` из приватных проектов;
    - авторизации в GitLab API от имени CI job.
docker login -u gitlab-ci-token -p $CI_JOB_TOKEN $CI_REGISTRY

### `CI_REGISTRY_TOKEN`
- похож на `CI_JOB_TOKEN`, но специфичен для docker pull/push;
- используется при взаимодействии с Registry (иногда явно, иногда GitLab делает сам).

> `CI_JOB_TOKEN` — это токен, который выдаётся на каждый job. Он используется для доступа к GitLab API, docker login, pull/push артефактов и общения между job’ами.  
> `CI_REGISTRY_TOKEN` — более специфичный, используется GitLab-ом при доступе к registry.  
> А `runner token` — это токен, с помощью которого сам runner регистрируется и запрашивает работу у GitLab."


[[CI_JOB_TOKEN, CI_REGISTRY_TOKEN, CI_COMMIT_SHA]]
[[Secrets, переменные, безопасность]]