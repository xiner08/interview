### 给定一个二叉树的根节点root，返回它的中序遍历

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var inorderTraversal = function(root) {
  // 返回值
  let result = []
  // 创建递归的函数
  var inorder = function(root){
    if(root === null){
      return
    }
    // 递归实现 
    inorder(root.left)
    // 将值保存起来
    result.push(root.val)
    inorder(root.right)
  }
  inorder(root)
  return result
}
```