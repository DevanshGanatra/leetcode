---
comments: true
edit_url: https://github.com/doocs/leetcode/edit/main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/README.md
---

# [剑指 Offer II 023. 两个链表的第一个重合节点](https://leetcode.cn/problems/3u1WK4)

## 题目描述

<!-- 这里写题目描述 -->

<p>给定两个单链表的头节点&nbsp;<code>headA</code> 和 <code>headB</code> ，请找出并返回两个单链表相交的起始节点。如果两个链表没有交点，返回 <code>null</code> 。</p>

<p>图示两个链表在节点 <code>c1</code> 开始相交<strong>：</strong></p>

<p><a href="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_statement.png" target="_blank"><img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_statement.png" style="height: 130px; width: 400px;" /></a></p>

<p>题目数据 <strong>保证</strong> 整个链式结构中不存在环。</p>

<p><strong>注意</strong>，函数返回结果后，链表必须 <strong>保持其原始结构</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><a href="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_example_1.png" target="_blank"><img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_example_1.png" style="height: 130px; width: 400px;" /></a></p>

<pre>
<strong>输入：</strong>intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
<strong>输出：</strong>Intersected at &#39;8&#39;
<strong>解释：</strong>相交节点的值为 8 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。
在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<p><a href="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_example_2.png" target="_blank"><img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_example_2.png" style="height: 136px; width: 350px;" /></a></p>

<pre>
<strong>输入：</strong>intersectVal&nbsp;= 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
<strong>输出：</strong>Intersected at &#39;2&#39;
<strong>解释：</strong>相交节点的值为 2 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。
在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
</pre>

<p><strong>示例&nbsp;3：</strong></p>

<p><a href="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_example_3.png" target="_blank"><img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcof2/%E5%89%91%E6%8C%87%20Offer%20II%20023.%20%E4%B8%A4%E4%B8%AA%E9%93%BE%E8%A1%A8%E7%9A%84%E7%AC%AC%E4%B8%80%E4%B8%AA%E9%87%8D%E5%90%88%E8%8A%82%E7%82%B9/images/160_example_3.png" style="height: 126px; width: 200px;" /></a></p>

<pre>
<strong>输入：</strong>intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
<strong>输出：</strong>null
<strong>解释：</strong>从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。
由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
这两个链表不相交，因此返回 null 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>listA</code> 中节点数目为 <code>m</code></li>
	<li><code>listB</code> 中节点数目为 <code>n</code></li>
	<li><code>0 &lt;= m, n &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= skipA &lt;= m</code></li>
	<li><code>0 &lt;= skipB &lt;= n</code></li>
	<li>如果 <code>listA</code> 和 <code>listB</code> 没有交点，<code>intersectVal</code> 为 <code>0</code></li>
	<li>如果 <code>listA</code> 和 <code>listB</code> 有交点，<code>intersectVal == listA[skipA + 1] == listB[skipB + 1]</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶：</strong>能否设计一个时间复杂度 <code>O(n)</code> 、仅用 <code>O(1)</code> 内存的解决方案？</p>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 160&nbsp;题相同：<a href="https://leetcode.cn/problems/intersection-of-two-linked-lists/">https://leetcode.cn/problems/intersection-of-two-linked-lists/</a></p>

## 解法

### 方法一：双指针

我们使用两个指针 $a$, $b$ 分别指向两个链表 $headA$, $headB$。

同时遍历链表，当 $a$ 到达链表 $headA$ 的末尾时，重新定位到链表 $headB$ 的头节点；当 $b$ 到达链表 $headB$ 的末尾时，重新定位到链表 $headA$ 的头节点。

若两指针相遇，所指向的结点就是第一个公共节点。若没相遇，说明两链表无公共节点，此时两个指针都指向 `null`，返回其中一个即可。

时间复杂度 $O(m+n)$，其中 $m$ 和 $n$ 分别是链表 $headA$ 和 $headB$ 的长度。空间复杂度 $O(1)$。

<!-- tabs:start -->

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        a, b = headA, headB
        while a != b:
            a = a.next if a else headB
            b = b.next if b else headA
        return a
```

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode a = headA, b = headB;
        while (a != b) {
            a = a == null ? headB : a.next;
            b = b == null ? headA : b.next;
        }
        return a;
    }
}
```

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* getIntersectionNode(ListNode* headA, ListNode* headB) {
        ListNode *a = headA, *b = headB;
        while (a != b) {
            a = a ? a->next : headB;
            b = b ? b->next : headA;
        }
        return a;
    }
};
```

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func getIntersectionNode(headA, headB *ListNode) *ListNode {
	a, b := headA, headB
	for a != b {
		if a == nil {
			a = headB
		} else {
			a = a.Next
		}
		if b == nil {
			b = headA
		} else {
			b = b.Next
		}
	}
	return a
}
```

```ts
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     val: number
 *     next: ListNode | null
 *     constructor(val?: number, next?: ListNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *     }
 * }
 */

function getIntersectionNode(headA: ListNode | null, headB: ListNode | null): ListNode | null {
    let a = headA;
    let b = headB;
    while (a != b) {
        a = a ? a.next : headB;
        b = b ? b.next : headA;
    }
    return a;
}
```

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function (headA, headB) {
    let a = headA;
    let b = headB;
    while (a != b) {
        a = a ? a.next : headB;
        b = b ? b.next : headA;
    }
    return a;
};
```

```swift
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.next = nil
 *     }
 * }
 */

class Solution {
    func getIntersectionNode(_ headA: ListNode?, _ headB: ListNode?) -> ListNode? {
        var a = headA
        var b = headB
        while a !== b {
            a = a == nil ? headB : a?.next
            b = b == nil ? headA : b?.next
        }
        return a
    }
}
```

<!-- tabs:end -->

<!-- end -->
