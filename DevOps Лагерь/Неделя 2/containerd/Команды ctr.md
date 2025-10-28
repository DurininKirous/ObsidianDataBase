---
sr-due: 2026-01-17
sr-interval: 81
sr-ease: 230
---
	
#sr-due 
```
ctr image pull docker.io/library/alpine:latest
ctr run -t --rm docker.io/library/alpine:latest test /bin/sh
ctr snapshot ls
ctr containers list
```
Данная утилита служит для отладки и разработки в основном. Для обычного пользования лучше более высокоуровневые утилиты типо docker cli использовать
[[Команды ctr]]
[[containerd]]