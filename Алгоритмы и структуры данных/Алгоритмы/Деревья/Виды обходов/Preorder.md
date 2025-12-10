---
sr-due: 2026-02-25
sr-interval: 84
sr-ease: 230
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