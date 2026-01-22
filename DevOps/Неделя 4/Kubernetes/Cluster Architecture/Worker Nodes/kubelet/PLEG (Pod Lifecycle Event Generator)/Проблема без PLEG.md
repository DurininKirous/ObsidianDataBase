---
sr-due: 2026-05-14
sr-interval: 126
sr-ease: 210
---

#sr-due 
- kubelet должен знать, что реально происходит с контейнерами
- Но kubelet сам контейнеры не запускает, он дёргат runtime (containerd/CRI-O) через CRI
- Если бы kubelet делал каждый раз полный ListContainers/ListPodSandbox и сравнивал со спеком - это было бы очень дорого и неэффективно
[[Проблема без PLEG]]
[[PLEG (Pod Lifecycle Event Generator)]]