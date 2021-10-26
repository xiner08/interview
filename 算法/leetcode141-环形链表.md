### 给定一个链表，判断链表是否有环
- 快慢指针,慢指针每次走一格，快指针每次走两格
```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function(head) {
  let slow = head
  let fast =head
  while(fast && fast.next){
    slow = slow.next
    fast = fast.next.next
    if(low === fast){
      return true
    }
  }
  return false
};
```
- 哈希表
```js
/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function(head) {
  let listMap = new Map()
  while(head){
      if(listMap.has(head)) return true
      listMap.set(head,true)
      head = head.next
  }
  return false
};
```