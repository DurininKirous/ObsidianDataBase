---
sr-due: 2025-12-06
sr-interval: 55
sr-ease: 210
---

#sr-due 
`docker` — это CLI-интерфейс (клиент), который:
- отправляет команды по HTTP API (Docker Engine API)
- общается с `dockerd` через сокет `/var/run/docker.sock`
- сам **не запускает контейнеры**, а делегирует всё `dockerd`

## Сокет
- по умолчанию: `/var/run/docker.sock`
- можно указать вручную:
    - `-H unix:///...`
    - `-H tcp://localhost:2375` (⚠️ опасно без TLS)

## Безопасность

> Доступ к `docker` = root-доступ к системе
- не открывай TCP сокет без TLS
- Доступ к `docker` CLI = доступ к сокету `/var/run/docker.sock`
- Этот сокет даёт **полный root-доступ к системе**, потому что:
  - можно запустить `--privileged` контейнер
  - примонтировать `/` хоста: `-v /:/mnt`
  - использовать `--pid=host`, `--net=host`, `--cap-add=ALL`
📛 Группа `docker` = `sudo`. Любой пользователь в ней может получить root.
### ⚠ Примеры опасных действий:

```bash
docker run --rm -it --privileged -v /:/mnt alpine chroot /mnt
```
[[docker cli]]
[[Неделя 2]]