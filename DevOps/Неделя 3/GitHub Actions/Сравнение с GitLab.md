---
sr-due: 2026-03-07
sr-interval: 128
sr-ease: 250
---

#sr-due 

| GitLab CI        | GitHub Actions       |
| ---------------- | -------------------- |
| `.gitlab-ci.yml` | `.github/workflows/` |
| `stages`         | `jobs/needs`         |
| `rules:`         | `if:`                |
| `include:`       | `workflow_call`      |
| `CI_JOB_TOKEN`   | `GITHUB_TOKEN`       |
[[Сравнение с GitLab]]
[[GitHub Actions]]