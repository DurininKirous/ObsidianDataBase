#sr-due 
- Сначала влево.
- Потом узел.
- Потом вправо.
- В **BST** даёт отсортированную последовательность.
```go
func inorder(root *TreeNode) {
    if root == nil {
        return
    }
    inorder(root.Left)       // Left
    fmt.Println(root.Val)    // Node
    inorder(root.Right)      // Right
}
```
[[Inorder]]
[[Виды обходов]]