---
sr-due: 2026-07-17
sr-interval: 223
sr-ease: 250
---

#sr-due 
Chroot — это механизм смены корня файловой системы для процесса
без PID, net, IPC namespaces и без cgroups.
не даёт настоящей изоляции.
Docker использует mount namespaces + pivot_root вместо chroot.
[[Chroot]]
[[Linux Primitives]]