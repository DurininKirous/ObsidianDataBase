---
sr-due: 2026-11-24
sr-interval: 320
sr-ease: 270
---

#sr-due 
Протокол для передачи гипертекста. Не имеет побайтовой структуры какой-либо, всё идёт как payload внутри TCP-сегмента.
Поля HTTP запроса:
Request Line: GET /path HTTP/1.1
Headers: Host, User-Agent, Accept,...
Пустая строка
Body (Для Put,Post)

Это строго client-pull модель.

[[HTTP]]
[[Сети]]