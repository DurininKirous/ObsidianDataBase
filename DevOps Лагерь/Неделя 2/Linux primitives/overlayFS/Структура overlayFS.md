---
sr-due: 2025-12-09
sr-interval: 91
sr-ease: 250
---

#sr-due 

| Элемент  | Для чего нужен                                                                                                  |
| -------- | --------------------------------------------------------------------------------------------------------------- |
| lowerdir | read-only слои                                                                                                  |
| upperdir | writeable слой                                                                                                  |
| workdir  | служебная директория для overlayFS (ядро Linux хранит временные данные для copy-up, whiteout и atomic операций) |
| merged   | результат: единый вид файловой системы                                                                          |
Пример:
`mount -t overlay overlay -o lowerdir=/base,upperdir=/changes,workdir=/work /merged`
Все файлы видны в /merged
Но:
- чтение берётся из upperdir если есть, иначе lowerdir
- запись всегда берётся в upperdir

[[Структура overlayFS]]
[[overlayFS]]