---
sr-due: 2026-05-08
sr-interval: 120
sr-ease: 210
---

#sr-due 
## Зачем его сделали
- Если у сервиса **много Pod’ов** (сотни/тысячи), объект Endpoints становится огромным (монолитный список).
- Обновления Endpoints = большие объёмы данных → нагрузка на etcd и API-server.
- Для масштабируемости придумали **EndpointSlice**: вместо одного здорового объекта — **несколько маленьких «слайсов»** (обычно до 100 адресов каждый).
Пример:
apiVersion: discovery.k8s.io/v1
kind: EndpointSlice
metadata:
  name: my-service-abc12
  labels:
    kubernetes.io/service-name: my-service
addressType: IPv4
ports:
- name: http
  port: 8080
endpoints:
- addresses: ["10.244.1.5"]
  conditions:
    ready: true
- addresses: ["10.244.2.7"]
  conditions:
    ready: false

[[EndpointSlice]]
[[Сущности]]