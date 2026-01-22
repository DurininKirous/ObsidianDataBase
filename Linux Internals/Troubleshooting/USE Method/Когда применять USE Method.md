---
sr-due: 2026-04-02
sr-interval: 84
sr-ease: 230
---

#sr-due 
- **Определи ресурс** — CPU, Disk, Memory, Network, Threads.
- **Для каждого измерь:**
    - **U** — занят ли он постоянно?
    - **S** — образуются ли очереди?
    - **E** — есть ли ошибки?
- **Инструменты:**
    - `vmstat`, `iostat`, `mpstat`, `sar`, `pidstat`
    - `perf`, `dstat`, `bpftrace`, `netstat`, `ss`
    - `top`, `htop`, `atop`, `glances`
    - Метрики Prometheus / Grafana (Node Exporter, cAdvisor и т.д.)
[[Когда применять USE Method]]
[[USE Method]]