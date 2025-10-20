# 🧠 Obsidian Knowledge Base

> Personal knowledge system for Linux, DevOps, System Design, Algorithms, and Databases.  
> Structured for systematic growth from low-level foundations to high-level architecture.

---

## 📁 Project Tree

```
├── Databases
│   ├── PostgreSQL
│   ├── SQL Language
│   ├── Бэкапы
│   └── Элементы реляционных баз данных
├── DevOps Лагерь
│   ├── Неделя 1
│   │   ├── LVM
│   │   ├── RAID
│   │   ├── SELinux
│   │   ├── Команды Linux
│   │   │   ├── iptables
│   │   │   └── Systemd
│   │   └── Сети
│   │       ├── ARP
│   │       ├── DNS
│   │       ├── HTTP
│   │       ├── HTTPS
│   │       ├── ICMP
│   │       ├── NTP
│   │       ├── TCP
│   │       └── UDP
│   ├── Неделя 2
│   │   ├── containerd
│   │   ├── Docker
│   │   │   ├── Docker Image
│   │   │   ├── Docker Network
│   │   │   └── Docker volumes
│   │   ├── docker cli
│   │   ├── dockerd
│   │   ├── Linux primitives
│   │   │   ├── Cgroups
│   │   │   ├── Namespaces
│   │   │   └── overlayFS
│   │   └── runc
│   ├── Неделя 3
│   │   ├── GitHub Actions
│   │   ├── GitLab CI CD
│   │   │   ├── Deployment
│   │   │   ├── gitlab-ci.yml
│   │   │   ├── GitLab Runner
│   │   │   └── Secrets, переменные, безопасность
│   │   └── Архитектура CI CD пайплайна
│   └── Неделя 4
│       └── Kubernetes
│           └── Cluster Architecture
│               ├── Architecture variations
│               │   └── Control plane deployment options
│               ├── Control Plane
│               │   ├── etcd
│               │   ├── kube-apiserver
│               │   │   └── Структура внутри apiserver
│               │   ├── kube-controller-manager
│               │   │   ├── Reconcile Loop
│               │   │   │   ├── Finalizers
│               │   │   │   ├── SharedInformerFactory и Informer
│               │   │   │   └── WorkQueue
│               │   │   └── Конкретные контроллеры
│               │   └── kube-scheduler
│               ├── DNS
│               │   └── CoreDNS
│               ├── Observability
│               │   ├── Kubernetes Autoscaling
│               │   │   ├── HPA
│               │   │   └── VPA
│               │   └── Архитектура Observability
│               ├── RBAC и Безопаность
│               ├── Volumes and Storage
│               │   ├── Ephmeral Volumes
│               │   ├── PV & PVC
│               │   └── StorageClass
│               ├── Worker Nodes
│               │   └── kubelet
│               │       ├── CNI
│               │       ├── CRI
│               │       ├── CSI
│               │       ├── PLEG (Pod Lifecycle Event Generator)
│               │       ├── Pod Lifecycle
│               │       ├── Probe
│               │       ├── QoS и Eviction
│               │       ├── Static Pod
│               │       ├── Конфигурация kubelet
│               │       ├── Ресурсные менеджеры
│               │       └── Управление образами и контейнерами
│               ├── Сеть
│               │   ├── kube-proxy
│               │   ├── NetworkPolicy
│               │   │   └── Базовые паттерны
│               │   └── Service
│               └── Сущности
│                   ├── Pod
│                   └── ReplicaSet
├── Linux Basics
├── Linux Internals
│   └── proc
│       └── Общая структура
├── Templates
├── Алгоритмы и структуры данных
│   ├── Leetcode
│   │   ├── Easy
│   │   ├── Hard
│   │   └── Medium
│   └── Алгоритмы
│       ├── Деревья
│       │   └── Виды обходов
│       └── Кучи
├── Кубачинский язык
├── Практика
└── Системный дизайн
    ├── Load Balancer
    │   └── Load Balancer
    ├── SLO-фрейм + RED USE
    ├── System Design Fundamenntals
    └── Сети → HTTP → API-дизайн
        └── Ниже API
```

---

## 🧩 About

This Obsidian vault organizes topics across **Linux internals, DevOps, Databases, Algorithms, and System Design**, following a layered learning model:

- **From low-level → high-level:**  
  Start with OS internals (processes, memory, filesystem), then build up to infrastructure, CI/CD, and system architecture.

- **From individual tools → systems thinking:**  
  Learn not just commands, but the principles behind how modern systems operate and scale.

- **Integrated roadmap:**  
  Matches your 3-month learning plan (Linux + DevOps + Go/Python + System Design).

---

## 🧠 Focus Areas

| Area | Description |
|------|--------------|
| 🐧 Linux Internals | Learn how the kernel manages memory, processes, filesystems, and /proc |
| ⚙️ DevOps Camp | Four-week deep dive into containerization, CI/CD, and Kubernetes architecture |
| 🧩 Databases | PostgreSQL internals, SQL fundamentals, and backups |
| 🧮 Algorithms | Practice LeetCode problems and key data structures |
| 🧠 System Design | Core distributed systems principles, scalability, reliability, SLO/RED/USE models |
| 🧾 Practice | Hands-on exercises and real-world notes |
| 💬 Кубачинский язык | Personal linguistic studies |

---

## 🧭 Notes

- Files ignored in version control (`.gitignore`):
  - Obsidian canvas files (`*.canvas`, `.png`, `My Roadmap 1.canvas`)
  - Temporary drafts (`Untitled*.md`)
  - Templates and scratch notes

