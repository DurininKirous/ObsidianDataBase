---
sr-due: 2025-12-03
sr-interval: 36
sr-ease: 230
---
	
#sr-due 
- Сначала влево.
- Потом вправо.
- В конце узел.
- Используется для удаления дерева (сначала дети, потом родитель).
```go
func postorder(root *TreeNode) {
    if root == nil {
        return
    }
    postorder(root.Left)     // Left
    postorder(root.Right)    // Right
    fmt.Println(root.Val)    // Node
}
```
[[Postorder]]
[[Виды обходов]]