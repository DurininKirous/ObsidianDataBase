- Это распределённое, консистентное key-value хранилище, куда kube-apiserver чтением/записью поддерживает всё состояние кластера
- Kubernetes использует etcd:
	- для хранения всех ресурсов (Pods, Nodes, Secrets, ConfigMaps, Deployments, CRDs, и т.д.)
	- для выдачи watch-стримов
	- для согласованной работы при множестве клиентов

Как реализован etcd внутри:
- Язык: Go
- Под капотом: `boltDB` для хранения, `grpc` для API
- Архитектура:
    - Frontend (gRPC API)
    - Backend (BoltDB snapshot + write-ahead log)
    - Raft (p2p консенсус)
[[Control Plane]]
[[etcd]]