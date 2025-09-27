---
sr-due: 2025-10-03
sr-interval: 9
sr-ease: 206
---

#sr-due 
Обрабатывает HTTP запросы: `GET /api/v1/pods`, `POST`, `DELETE`, `WATCH`
Для каждого ресурса описан RESTStorage:
- Create
- Update
- Delete
- List
- Watch
Он превращает HTTP -> internal runtime объект -> записывает через StorageInterface в etcd.
Каждый API Group/version/resource регистрируется при запуске.
Как:
- Роутинг запросов: `/api/v1/pods` → `PodStorage`
- Каждый storage реализует `Create`, `Update`, `List`, `Watch` и т.д.
- Использует стратегию сериализации (`JSON`, `protobuf`)
- Через `StorageInterface` отправляет в etcd
Без него:
- Невозможно обрабатывать никакие ресурсы
- API будет пустым

[[RESTStorage (API Handlers)]]
[[Структура внутри apiserver]]