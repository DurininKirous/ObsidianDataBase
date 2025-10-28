---
sr-due: 2025-12-05
sr-interval: 38
sr-ease: 230
---

#sr-due 
**Идея:** обход послойно (через очередь).
- Используется для:
    - Кратчайший путь в невзвешенном графе.
    - Проверка двудольности.
    - Level-order traversal.
```go
func bfs(start int, graph map[int][]int) {
    visited := make(map[int]bool)
    queue := []int{start}
    visited[start] = true

    for len(queue) > 0 {
        node := queue[0]
        queue = queue[1:]
        for _, nei := range graph[node] {
            if !visited[nei] {
                visited[nei] = true
                queue = append(queue, nei)
            }
        }
    }
}
```
[[BFS (Breadth-First Search)]]
[[Деревья]]