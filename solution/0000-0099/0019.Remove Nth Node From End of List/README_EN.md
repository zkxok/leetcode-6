# [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list)

[中文文档](/solution/0000-0099/0019.Remove%20Nth%20Node%20From%20End%20of%20List/README.md)

## Description

<p>Given a linked list, remove the <em>n</em>-th node from the end of list and return its head.</p>

<p><strong>Example:</strong></p>

<pre>

Given linked list: <strong>1-&gt;2-&gt;3-&gt;4-&gt;5</strong>, and <strong><em>n</em> = 2</strong>.



After removing the second node from the end, the linked list becomes <strong>1-&gt;2-&gt;3-&gt;5</strong>.

</pre>

<p><strong>Note:</strong></p>

<p>Given <em>n</em> will always be valid.</p>

<p><strong>Follow up:</strong></p>

<p>Could you do this in one pass?</p>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        dummy = ListNode(next=head)
        p = q = dummy
        for i in range(n):
            p = p.next
        while p.next:
            p, q = p.next, q.next
        q.next = q.next.next
        return dummy.next
```

### **Java**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);
        ListNode p = dummy, q = dummy;
        while (n-- > 0) {
            p = p.next;
        }
        while (p.next != null) {
            p = p.next;
            q = q.next;
        }
        q.next = q.next.next;
        return dummy.next;
    }
}
```

### **C++**

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* dummy = new ListNode(0, head);
        ListNode* p = dummy;
        ListNode* q = dummy;
        while (n-- > 0) {
            p = p->next;
        }
        while (p->next != nullptr) {
            p = p->next;
            q = q->next;
        }
        q->next = q->next->next;
        return dummy->next;
    }
};
```

### **Go**

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func removeNthFromEnd(head *ListNode, n int) *ListNode {
    dummy := &ListNode{Val:0, Next:head}
    p := dummy
    q := dummy
    for n > 0 {
        p = p.Next
        n--
    }
    for p.Next != nil {
        p = p.Next
        q = q.Next
    }
    q.Next = q.Next.Next
    return dummy.Next
}
```

### **...**

```

```

<!-- tabs:end -->
