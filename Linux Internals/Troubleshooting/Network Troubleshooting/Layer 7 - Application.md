---
sr-due: 2026-02-03
sr-interval: 57
sr-ease: 250
---

#sr-due 
**Вопросы:** приложение отвечает корректно? что в логах/метриках?
```bash
curl -v http://127.0.0.1:8080/health   # curl — запрос к приложению/healthcheck с деталями протокола
journalctl -u myservice --since -10m   # journalctl — логи unit’а systemd за период
```
- 2xx локально, 5xx снаружи → балансер/прокси/головы таймаутов.
- Таймауты на L7 при нормальном L4 → медленные бэкенды/DNS.
[[Layer 7 - Application]]
[[Network Troubleshooting]]