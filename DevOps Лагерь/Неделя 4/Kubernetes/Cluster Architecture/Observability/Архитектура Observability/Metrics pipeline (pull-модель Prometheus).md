---
sr-due: 2025-11-11
sr-interval: 14
sr-ease: 210
---

#sr-due 
- Service discovery в k8s (kubernetes_sd_config): Prometheus сам находит Pod/Servicce/Endpoints по лейблам/анотациям
- Relabeling: фильтрует и нормализует таргеты
- Scrape: регулярные GET к /metrics всех таргетов, парсинг Prometheus-текста, запись в TSDB
- TSDB:
	- WAL (журнал), блоки (обычно 2 часа), мерж-компакции, retention, cardinality control
	- Проблема - взрыв кардинальности (метки с high cardinality: pod, container, path, user_id) -> нужно проектировать labels аккуратно
Кардинальность = **количество уникальных комбинаций меток (label values)**, которые создают отдельные time-series в базе Prometheus.

>Минимальный прод-набор метрик: kubelet/kube-proxy, node-exporter, kube-state-metrics, app `/metrics`.

[[Metrics pipeline (pull-модель Prometheus)]]
[[Архитектура Observability в Kubernetes]]