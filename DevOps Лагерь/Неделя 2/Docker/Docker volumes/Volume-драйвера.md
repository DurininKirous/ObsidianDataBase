---
sr-due: 2025-08-22
sr-interval: 25
sr-ease: 270
---

#sr-due 
Docker поддерживает volume-драйверы:
- `local` (по умолчанию)
- `nfs`, `sshfs`, `smb`, `s3` (через плагин)
- custom через volume plugin API
docker volume create --driver local --opt type=nfs ...
[[Volume-драйвера]]
[[Docker volumes]]