---
sr-due: 2025-09-15
sr-interval: 2
sr-ease: 210
---

#sr-due 
etcd - один из немногих хранилищ с встроенной подержкой watch API.
- каждый объект имеет mod_revision
- каждый клиент может открыть Watch(key, from_revision)
- используется long-lived streaming gRPC connection
Kube-apiserver держит один watch, и рассылает своих клиентов (controller-manager, scheduler, etc.)
[[Watch-механизм]]
[[etcd]]