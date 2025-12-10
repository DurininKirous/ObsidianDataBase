---
sr-due: 2026-01-26
sr-interval: 52
sr-ease: 250
---

#sr-due 
Когда память исчерпана и своп переполнен, Linux запускает OOM Killer.
Он выбирает процесс с наибольшим oom_score и завершает его.

Проверка "жертвы":
```bash
dmesg | grep -i oom
cat /proc/<pid>/oom_score
```
- Чем выше score, тем больше вероятность, что процесс будет убит
- /proc/pid/oom_adj - можно понизить приоритет "убийства" для критичных сервисов

Типичные причины OOM:
- Утечка памяти в процессе
- Слишком много процессов
- Overcommit настроен агрессивно (vm.overcommit_memory = 2 может спасать)
- Плохой лимит cgroup
[[OOM Killer]]
[[Memory Troubleshooting]]