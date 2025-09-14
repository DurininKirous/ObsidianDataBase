---
sr-due: 2025-09-14
sr-interval: 2
sr-ease: 230
---

#sr-due 
Контроллер подключает свой обработчик.
Именно эти функции **вызываются, когда Reflector замечает изменения**   
Именно здесь контроллер **ставит объект в WorkQueue** (по ключу, например `"default/my-pod"`)
[[EventHandlerFuncs]]
[[SharedInformerFactory и Informer]]