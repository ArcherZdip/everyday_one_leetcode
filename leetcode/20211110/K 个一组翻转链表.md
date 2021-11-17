## 题目描述
[https://leetcode-cn.com/problems/reverse-nodes-in-k-group/](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)


## 解题思路
[https://leetcode-cn.com/problems/reverse-nodes-in-k-group/solution/k-ge-yi-zu-fan-zhuan-lian-biao-by-leetcode-solutio/](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/solution/k-ge-yi-zu-fan-zhuan-lian-biao-by-leetcode-solutio/)

## 解题代码
#### PHP
```php
/**
 * Definition for a singly-linked list.
 * class ListNode {
 *     public $val = 0;
 *     public $next = null;
 *     function __construct($val = 0, $next = null) {
 *         $this->val = $val;
 *         $this->next = $next;
 *     }
 * }
 */
class Solution {

    /**
     * @param ListNode $head
     * @param Integer $k
     * @return ListNode
     */
    function reverseKGroup($head, $k) {
       $rv = new ListNode();
        $node = $rv;
        while ($head != null) {
            $stack = [];
            $i = $k;
            while ($i-- > 0 && $head != null) {
                $stack[] = $head;
                $head = $head->next;
            }

            if ($i < 0) {
                while (!empty($stack)) {
                    $node->next = array_pop($stack);
                    $node = $node->next;
                }
            } else {
                $node->next = $stack[0];
                break;
            }
            
            $node->next = null;
        }

        return $rv->next;
    }
}
```

#### GO
```go
// 官方解题
func reverseKGroup(head *ListNode, k int) *ListNode {
    hair := &ListNode{Next: head}
    pre := hair

    for head != nil {
        tail := pre
        for i := 0; i < k; i++ {
            tail = tail.Next
            if tail == nil {
                return hair.Next
            }
        }
        nex := tail.Next
        head, tail = myReverse(head, tail)
        pre.Next = head
        tail.Next = nex
        pre = tail
        head = tail.Next
    }
    return hair.Next
}

func myReverse(head, tail *ListNode) (*ListNode, *ListNode) {
    prev := tail.Next
    p := head
    for prev != tail {
        nex := p.Next
        p.Next = prev
        prev = p
        p = nex
    }
    return tail, head
}
```