---
sr-due: 2025-10-14
sr-interval: 1
sr-ease: 230
---

#sr-due 
```yaml
updatePolicy:
  updateMode: "Off" | "Initial" | "Auto" | "Recreate"
```
- **Off** — только рекомендации.
- **Auto** — пересоздаёт поды с новыми requests.
- **Recreate** — жёстко убивает и пересоздаёт (опасно).
- **Initial** — меняет ресурсы только на старте.

[[Типы mode]]
[[VPA]]