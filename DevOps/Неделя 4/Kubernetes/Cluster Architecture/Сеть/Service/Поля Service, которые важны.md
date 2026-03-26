---
sr-due: 2026-08-12
sr-interval: 184
sr-ease: 230
---

#sr-due 
apiVersion: v1
kind: Service
metadata:
  name: web
spec:
  selector: { app: web }   # какие Pod'ы включает
  type: ClusterIP          # тип сервиса (ClusterIP | NodePort | LoadBalancer | ExternalName)
  clusterIP: 10.96.3.21    # VIP (обычно назначается автоматически)
  ports:
    - name: http
      port: 80             # порт сервиса (VIP:port, куда ходят клиенты)
      targetPort: 8080     # порт в Pod (куда реально придёт трафик)
      nodePort: 30080      # (только для NodePort/LoadBalancer) порт на ноде
  sessionAffinity: ClientIP

- **`port`** — «внешний» порт сервиса (на VIP).
- **`targetPort`** — порт контейнера; можно указать **имя** порта из PodSpec.
- **`clusterIP`** — VIP из подсети Service CIDR (immutable; исключение — headless).
- **`type`**:
    - `ClusterIP` — доступен только внутри кластера.
    - `Headless` (`clusterIP: None`) — **без VIP**; DNS отдаёт **список Pod IP** (часто для StatefulSet).
    - `NodePort` — открывает порт на **каждой ноде** (`30000–32767` по умолчанию).
    - `LoadBalancer` — создаёт внешний LB (через облачный контроллер), который **под капотом** ходит в NodePort.
- **`sessionAffinity: ClientIP`** — «прилипание» клиента к одному Pod (см. conntrack ниже).
[[Поля Service, которые важны]]
[[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 4/Kubernetes/Cluster Architecture/Сеть/Service/Service]]