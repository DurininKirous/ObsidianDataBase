---
sr-due: 2025-09-15
sr-interval: 43
sr-ease: 290
---

#sr-due 
Проверить режим: getenforce
Перевести в Permissive: setenforce 0
Вернуть в enforcing: setenforce 1
Изменить режим на постоянку: 
- vim /etc/selinux/config
- SELINUX=enforcing/permissive/disabled
[[Типовые практические приёмы SELinux]]
[[SELinux]]