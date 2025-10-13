---
sr-due: 2025-10-22
sr-interval: 13
sr-ease: 230
---

#sr-due 
**Идея:** идти как можно глубже, пока не упрёмся, потом backtrack
- Реализация через рекурсию или стек.
- Используется для:
    - Проверка связности.
    - Поиск цикла.
    - Классификация рёбер (tree/back/cross).
```go
func dfs(node int, visited []bool, graph map[int][]int) {
    if visited[node] { return }
    visited[node] = true
    for _, nei := range graph[node] {
        dfs(nei, visited, graph)
    }
}
```

[[DFS — Depth-First Search]]
[[Деревья]]