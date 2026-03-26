---
sr-due: 2026-12-12
sr-interval: 286
sr-ease: 250
---

#sr-due 
- Сначала обрабатываем узел (`Node`).
- Потом идём влево (`Left`).
- Потом вправо (`Right`).
- Используется для копирования дерева, сериализации.
```go
func preorder(root *TreeNode) {
    if root == nil {
        return
    }
    fmt.Println(root.Val)    // Node
    preorder(root.Left)      // Left
    preorder(root.Right)     // Right
}
```
[[Preorder]]
[[Виды обходов]]