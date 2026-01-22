---
created: 2026-01-06 20:09
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-05-05
sr-interval: 119
sr-ease: 206
---
### 💡 The What
*Что это?*
Центральный компонент API Server в Kubernetes, который реализует интерфейс `rest.Storage`и обеспечивает обработку [[HTTP]]-запросов к ресурсам кластера. Каждый ресурс ([[Pod]], [[ObsidianDataBase/DevOps/Неделя 4/Kubernetes/Cluster Architecture/Сеть/Service/Service|Service]], [[ObsidianDataBase/DevOps/Неделя 4/Kubernetes/Cluster Architecture/Сущности/Deployment|Deployment]]) имеет свой RESTStorage экземпляр, зарегистрированный при старте API Server.

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
- **Роутинг**: Маппинг `/api/v1/pods` → `PodStorage` через registry при инициализации API Server[](https://habr.com/ru/articles/719598/)​
- **Трансформация**: HTTP request → internal runtime object → serialization (JSON/protobuf) → StorageInterface → etcd[](https://itnext.io/deep-dive-into-how-kubernetes-rest-api-works-517c86f1640b)​
- **CRUD операции**: Реализует `Create`, `Update`, `Delete`, `List`, `Watch` через `rest.StandardStorage` interface[](https://habr.com/ru/articles/719598/)​
- **Storage versioning**: Каждый объект хранится в одной активной storage version, reads конвертируются в API representation, writes обновляют версию[](https://kubernetes.io/docs/concepts/overview/working-with-objects/storage-version/)​
- **Абстракция персистентности**: `storage.Interface` методы возвращают только error, данные передаются через pointer parameters для оптимизации

---
### ⚔️ VS / Trade-offs
*С чем сравнить? Плюсы/Минусы.*
- **VS прямой etcd доступ**: RESTStorage добавляет слой абстракции с validation, versioning, serialization стратегиями — снижает производительность, но обеспечивает consistency и backward compatibility
- **Trade-off**: Unified interface для всех ресурсов упрощает разработку, но требует boilerplate кода для каждого нового resource type


---
### 🔗 Connections
- **Родитель**: [[kube-apiserver]]
- **Влияет на**: [[etcd]]
- **Инсайт**: 
