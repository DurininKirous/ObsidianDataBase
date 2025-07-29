---
sr-due: 2025-09-09
sr-interval: 43
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