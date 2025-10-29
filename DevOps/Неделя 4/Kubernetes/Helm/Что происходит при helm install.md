---
sr-due: 2025-10-31
sr-interval: 2
sr-ease: 230
---

#sr-due 
Ментальный трейс:
1. Helm CLI читает `Chart.yaml` + values.yaml (+ твои -f/--set) 
2. Прогоняет Go-шаблоны -> получает плоские kubernetes-манифесты
3. Создаёт Release: по сути - применяет манифесты через Kubernetes API (kubectl не зовёт, работает напрямую по kubeconfig)
4. Сохраняет историю релиза в кластере (Helm v3):
	1. объект-хранилище: Secret в namespace релиза,
	2. имя вида: sh.helm.release.v1.release-name.vrevesion,
	3. внутри - зашифрованныеы/сжатые данные о манифестах, values, ревизии, статусе
> В Helm v3 нет Tiller, всё клиент-сайд, авторизация - твои kubeconfig/RBAc


[[Что происходит при helm install]]
[[Helm]]