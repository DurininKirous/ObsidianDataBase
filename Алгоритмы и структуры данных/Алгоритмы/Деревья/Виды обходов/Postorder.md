---
sr-due: 2026-02-24
sr-interval: 83
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