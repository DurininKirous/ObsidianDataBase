---
sr-due: 2025-11-17
sr-interval: 12
sr-ease: 230
---

#sr-due 
**PDB — это “бюджет на перерывы” для подов.**  
Он говорит Kubernetes:
> “Допустимо, чтобы одновременно было недоступно не больше X подов этого приложения.”

Это нужно, чтобы во время обновлений, drain нод или maintenance сервис **оставался доступным**.

```yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: web-pdb
spec:
  maxUnavailable: 1
  selector:
    matchLabels:
      app: web
```
→ теперь Kubernetes гарантирует, что **в один момент времени максимум 1 под** может быть убит/эвиктнут.

> Это значит: всегда минимум 2 пода из 3 должны быть живы.

Примеры настроек:

| Поле                | Значение                            | Что значит                  |
| ------------------- | ----------------------------------- | --------------------------- |
| `maxUnavailable: 1` | максимум 1 под может быть убит      | минимум N-1 подов останется |
| `minAvailable: 2`   | минимум 2 пода должны быть доступны | безопасно при drain, HPA    |
## 🧠 Под капотом
PDB — объект, который отслеживается контроллером `disruption-controller`.  
Он записывает:
- сколько подов всего под контролем (`expectedPods`);
- сколько сейчас живы (`currentHealthy`);
- сколько можно безопасно эвиктить (`disruptionsAllowed`).
Проверка:
```
kubectl get pdb
kubectl describe pdb web-pdb
```
```
Allowed disruptions: 1
Current healthy: 3
Desired healthy: 2
Total pods: 3
```
[[PodDisruptionBudget]]
[[Worker Nodes]]