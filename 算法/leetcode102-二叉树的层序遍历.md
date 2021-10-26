### 给你一个二叉树，请你返回其按层序遍历得到的节点值
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
 * @return {number[][]}
 */
var levelOrder = function(root) {
    let res = [],q = []
    if(root === null) return res
    q.push(root)
    while(q.length !== 0){
        // 储存这一行的值
        let curleval = []
        // 保存q的长度
        let length = q.length
        for(let i = 0; i < length; i++){
            let node = q.shift()
            curleval.push(node.val)
            node.left && q.push(node.left)
            node.right && q.push(node.right)
        }
        // 将每一行的值push到返回的数组中
        res.push(curleval)
    }
    return res
};
```
