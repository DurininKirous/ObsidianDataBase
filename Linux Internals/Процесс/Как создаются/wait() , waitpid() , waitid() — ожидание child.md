---
sr-due: 2026-03-26
sr-interval: 77
sr-ease: 210
---

#sr-due 
**Зачем:** снять «зомби» и получить статус завершения.
- `wait(int *status)` — ждёт _любой_ дочерний; возвращает PID, пишет статус.
- `waitpid(pid, &status, options)`:
    - `pid > 0` — ждать конкретного PID.
    - `pid == 0` — любого из текущей группы процессов.
    - `pid == -1` — любого (как `wait`).
    - `options`: `WNOHANG` (не блокироваться), `WUNTRACED` (получать остановки), `WCONTINUED` (продолжение после `SIGCONT`).
- `waitid(idtype, id, siginfo_t *infop, options)` — более гибкая, статус в `siginfo`, можно `WNOWAIT`.

**Разбор статуса (макросы):**
- `WIFEXITED(s)` → обычный выход; `WEXITSTATUS(s)` → код 0..255.
- `WIFSIGNALED(s)`; `WTERMSIG(s)` — убит сигналом; `WCOREDUMP(s)` — есть core.
- `WIFSTOPPED(s)`/`WSTOPSIG(s)` и `WIFCONTINUED(s)` — job-control.

**SIGCHLD и гонки:** надёжный паттерн — обрабатывать `SIGCHLD`, вызывать `waitpid(-1, …, WNOHANG)` в цикле, пока забираются все завершившиеся.
[[wait() , waitpid() , waitid() — ожидание child]]
[[Как создаются]]