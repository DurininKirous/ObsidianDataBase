---
sr-due: 2026-01-12
sr-interval: 55
sr-ease: 190
---

#sr-due 
etcd - один из немногих хранилищ с встроенной подержкой watch API.
- каждый объект имеет mod_revision
- каждый клиент может открыть Watch(key, from_revision)
- используется long-lived streaming gRPC connection
Kube-apiserver держит один watch, и рассылает своих клиентов (controller-manager, scheduler, etc.)
[[Watch-механизм]]
[[etcd]]