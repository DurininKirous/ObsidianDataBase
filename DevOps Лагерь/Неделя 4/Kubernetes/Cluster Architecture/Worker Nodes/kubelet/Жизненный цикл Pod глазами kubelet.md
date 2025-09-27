---
sr-due: 2025-10-02
sr-interval: 8
sr-ease: 190
---

#sr-due 
1. Scheduler назначает Pod на ноду -> в API появляется `spec.nodeName`
2. kubelet видит новый Pod по watch и кладёт его в worker 
3. SyncPod цикл:
	1. Подготовить тома, смонтировать Secret/ConfigMap и т.п.
	2. Создать Pod SandBox (pause-контейнер, сетевой namespace, IP через CNI)
	3. Создать и запустить контейнеры Pod'а
	4. Запустить пробы
	5. Проставить статус Pod'а/контейнеров в API
4. В работе kubelet:
	1. Следит за пробами, делает рестарты по restartPolicy, применяет бэкофф
	2. Обрабатывает preStop + graceful shutdown при удалении
	3. Участвует в эвикциях при давлении ресурсов
5. При удалении Pod: SIGTERTM -> terminationGracePeriodSeconds -> SIGKILL, CNI DEL, размонтаж томов
[[Жизненный цикл Pod глазами kubelet]]
[[kubelet]]