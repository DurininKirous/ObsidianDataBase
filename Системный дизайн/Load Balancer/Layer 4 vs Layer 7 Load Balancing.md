---
created: 2026-01-07 12:12
tags:
  - status/seed
  - type/concept
  - domain/linux
  - sr-due
sr-due: 2026-04-20
sr-interval: 103
sr-ease: 230
---
### 💡 The What
*Что это?*
Сравнение LB на 4 уровне OSI и на 7

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
#### Layer 4 (Transport Layer) - быстрый, но "тупой"
Работает на уровне [[TCP]], [[UDP]], не смотрит содержимое [[HTTP]]:

Client -> LB -> Server
		(Видит только IP:Port)

Плюсы: очень быстрый
Минусы: Не может маршрутизировать по URL, Headers, cookies

Примеры: AWS Network Load Balancer, HAProxy в TCP Mode

#### Layer 7 (Application Layer) - умный, но медленнее
Работает на уровне HTTP, понимает запросы:
```
GET /api/users -> Server 1 (API Backend)
GET /imgaes/   -> Server 2 (Static files)
GET /admin/    -> Server 3 (Admin Panel)
```

Может маршрутизировать по :
- URL Path
- HTTP Headers
- Cookies
- Request Method

Дополнительные возможности:
- SSL Termination
- Compression
- Caching
- Rate limiting
- WAF (Web Application Firewall)

Примеры: AWS Application Load Balancer, NGINX, Envoy

---
### 🔗 Connections
- **Родитель**: [[Load Balancer]]
- **Влияет на**: [[Алгоритмы балансировки]], [[Где размещать Load Balancer]]
