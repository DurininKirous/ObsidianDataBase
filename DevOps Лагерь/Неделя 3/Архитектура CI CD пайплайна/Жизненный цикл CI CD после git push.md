---
sr-due: 2025-10-25
sr-interval: 46
sr-ease: 228
---

#sr-due 
После пушинга запускается цепочка системных процессов, которая выглядит так:
1. GitLab Web получает событие
	- GitLab (Rails часть) получает git push через:
		- Git over SSH или HTTP
		- ивенты обрабатываются Gitaly (сервис управления Git-репами)
	- GitLab фиксирует pipeline trigger, если:
		- в репозитории есть .gitlab-ci.yml
		- CI/CD включён в настройках проекта
2. GitLab CI анализирует .gitlab-ci.yml
	- GitLab парсит .gitlab-ci.yml
	- Генерирует DAG-представление пайплайна
	- Строит pipeline
	- Проверяется rules:/only:/except:, чтобы понять - запускать пайплайн или нет
	- GitLab создаёт запись о pipeline и jobs в базе данных PostgreSQL
3. GitLab размещает пайплайн в очередь
	- Jobs попадают в Redis очередь (ci:builds)
	- Они ждут, пока GitLab Runner спросит: "Есть для меня работа?"

[[Жизненный цикл CI CD после git push]]
[[Архитектура CI CD пайплайна]]