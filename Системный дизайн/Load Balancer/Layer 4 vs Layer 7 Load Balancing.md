---
sr-due: 2025-12-12
sr-interval: 32
sr-ease: 230
---

#sr-due 
#### Layer 4 (Transport Layer) - быстрый, но "тупой"
Работает на уровне TCP, UDP, не смотрит содержимое HTTP:

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
[[Layer 4 vs Layer 7 Load Balancing]]
[[Load Balancer]]