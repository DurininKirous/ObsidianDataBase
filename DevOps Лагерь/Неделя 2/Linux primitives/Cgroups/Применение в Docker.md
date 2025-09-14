---
sr-due: 2025-11-05
sr-interval: 57
sr-ease: 210
---

#sr-due 
Когда делаем:
`docker run -d --name myapp --memory=200M --cpus=0.5 nginx`
под капотом Docker делает примерно такой алгоритм:
- runc создаёт cgroup-директорию в /sys/fs/cgroup
- в неё пишет echo "200" > memory.max
- echo "50000 100000" > cpu.max
- Запускает контейнерный процесс и сразу пишет его PID в cgroup.procs
- Всё, контейнер ограничен физически по ресурсам ядром Linux через cgroups

### Посмотреть в контейнере

Если войти в контейнер и сделать
`cat /proc/self/cgroup`
увидим, что он приписан к своей cgroup:
`0::/docker/12a34bc56...`

Kubernetes делает примерно то же самое, когда создаёт под через kubelet.
[[Применение в Docker]]
[[Cgroups]]