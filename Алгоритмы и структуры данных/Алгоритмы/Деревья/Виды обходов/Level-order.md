---
sr-due: 2025-10-23
sr-interval: 14
sr-ease: 230
---

#sr-due 
**Level-order (BFS)**
- Обход по уровням.
- Реализуется через очередь.
```go
func levelOrder(root *TreeNode) {
    if root == nil {
        return
    }
    queue := []*TreeNode{root}
    for len(queue) > 0 {
        node := queue[0]
        queue = queue[1:]
        fmt.Println(node.Val)
        if node.Left != nil {
            queue = append(queue, node.Left)
        }
        if node.Right != nil {
            queue = append(queue, node.Right)
        }
    }
}
```
[[Level-order]]
[[Виды обходов]]