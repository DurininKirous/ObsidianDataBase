---
created: 2026-01-28 17:34
tags:
  - status/seed
  - type/concept
  - domain/k8s
  - sr-due
sr-due: 2026-07-22
sr-interval: 175
sr-ease: 230
---
### 💡 The What
*Что это?*
Static Pod из-за своих отличий от обычных подов не используются для развертывания обычных сервсов. Они используются для более специфичных задач

### ⚙️ The Why & How
*Инженерная суть. Механика. Зачем это нужно?*
Что кладут:
- Компоненты [[Control Plane]] (kubeadm так и делает):  
    [[kube-apiserver]], [[kube-controller-manager]], [[kube-scheduler]], [[etcd]].
- Томá обычно [[hostPath]] (сертификаты, конфиги, сокеты), чтобы процесс видел файловую систему ноды.

---
### 🔗 Connections
- **Родитель**: [[Static Pods]], [[Static Pod в K8S]]
- **Влияет на**: [[Control Plane]]
