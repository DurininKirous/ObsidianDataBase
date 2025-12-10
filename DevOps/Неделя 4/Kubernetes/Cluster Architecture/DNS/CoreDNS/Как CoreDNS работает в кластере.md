---
sr-due: 2026-02-19
sr-interval: 87
sr-ease: 230
---

#sr-due 
- Pod хочет обратиться к `db.default.svc.cluster.local`.
- В `/etc/resolv.conf` Pod’а прописан nameserver = ClusterIP CoreDNS.
- Запрос уходит в CoreDNS pod.
- Плагин `kubernetes` спрашивает у kube-apiserver: «Что за сервис `db` в `default`?»
- CoreDNS возвращает **ClusterIP** сервиса.
- Дальше kube-proxy перенаправляет этот IP на Pod’ы.
[[Как CoreDNS работает в кластере]]
[[CoreDNS]]