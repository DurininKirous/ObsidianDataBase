---
sr-due: 2026-02-11
sr-interval: 87
sr-ease: 230
---

#sr-due 
Это **подсистема подписки и кеширования ресурсов**, которая обеспечивает производительность, реактивность и масштабируемость контроллеров.

## Что такое `SharedInformerFactory`
Это **фабрика**, создающая informer’ы для всех типов ресурсов:
	factory := informers.NewSharedInformerFactory(clientset, resyncPeriod)
	podInformer := factory.Core().V1().Pods().Informer()
📌 Один factory → много informer'ов  
📌 Все informer'ы **делят один client-go кэш и connection pool**  
📌 Один informer на ресурс → **все контроллеры его используют совместно**
### Зачем нужен informer?
Kubernetes — **event-driven система**.  
Контроллеры **не опрашивают API Server напрямую**, потому что это:
- создаёт нагрузку
- даёт устаревшие данные
- нарушает масштаб
Вместо этого используется:

> ✅ **Informer** — механизм, который:
> - подписывается на изменения ресурсов (`List + Watch`)
> - **ведёт локальный кеш**
> - уведомляет контроллеры о событиях (`Add`, `Update`, `Delete`)

[[SharedInformerFactory и Informer]]
[[Watch (подписка на изменения)]]