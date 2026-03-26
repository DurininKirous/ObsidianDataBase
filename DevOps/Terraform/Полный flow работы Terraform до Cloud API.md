---
created: 2026-01-12 20:52
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-03-19
sr-interval: 18
sr-ease: 229
---
### 💡 The What
*Что это?*
Описание работы последовательности terraform init -> plan -> apply

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- terraform init: [[Core модуль в Terraform]] скачивает провайдеры, handshake (обмен портами для gRPC)
- Plan: HCL -> DAG -> вычисление значений (eval vars/refs) -> RPC к провайдеру (Read/Plan) -> .tfplan файл с diff
- Apply: plan -> DAG -> RPC ApplyResource -> провайдер шлёт [[HTTP]] в Cloud API -> обновляет state (JSON с текущим состоянием всей infra: ресурсы + их ID/attrs). State хранится локально или в S3 с locking 

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS [[...]]**: 
- **Trade-off**: 


---
### 🔗 Connections
- **Родитель**: [[...]]
- **Влияет на**: [[...]]
- **Инсайт**: 
	- **State** — источник бед: хранит реальное состояние (ID ресурсов из API), конфликты от concurrent apply решает locking.
	- **Blast radius** (радиус ущерба): DAG минимизирует, но count/for_each создаёт динамические подграфы — изменения в одном instance не трогают другие.
	- **Отладка**: `TF_LOG=DEBUG` покажет RPC и API calls; `terraform graph` — DOT‑файл графа для визуализации
