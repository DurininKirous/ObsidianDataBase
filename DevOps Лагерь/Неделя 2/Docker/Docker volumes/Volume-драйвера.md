---
sr-due: 2025-12-03
sr-interval: 88
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