#sr-due 
1. GitLab отдаёт Job в Redis
2. Runner делает `POST /api/v4/jobs/request`
3. GitLab отдаёт Job, если совпадает tag
4. Runner запускает job, и

pre_clone_script     # подготовка окружения
↓
clone_repo           # git clone проекта
↓
before_script        # если задано
↓
script               # основное тело (например, make docker)
↓
after_script         # всегда выполняется
↓
cleanup / trace / статус → API

[[Как Runner исполняет job - жизненный цикл]]
[[GitLab Runner]]