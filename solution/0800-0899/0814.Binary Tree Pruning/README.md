---
comments: true
difficulty: 中等
edit_url: https://github.com/doocs/leetcode/edit/main/solution/0800-0899/0814.Binary%20Tree%20Pruning/README.md
tags:
    - 树
    - 深度优先搜索
    - 二叉树
---

# [814. 二叉树剪枝](https://leetcode.cn/problems/binary-tree-pruning)

[English Version](/solution/0800-0899/0814.Binary%20Tree%20Pruning/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给你二叉树的根结点&nbsp;<code>root</code>&nbsp;，此外树的每个结点的值要么是 <code>0</code> ，要么是 <code>1</code> 。</p>

<p>返回移除了所有不包含 <code>1</code> 的子树的原二叉树。</p>

<p>节点 <code>node</code> 的子树为 <code>node</code> 本身加上所有 <code>node</code> 的后代。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/0800-0899/0814.Binary%20Tree%20Pruning/images/1028_2.png" style="width: 500px; height: 140px;" />
<pre>
<strong>输入：</strong>root = [1,null,0,0,1]
<strong>输出：</strong>[1,null,0,null,1]
<strong>解释：</strong>
只有红色节点满足条件“所有不包含 1 的子树”。 右图为返回的答案。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/0800-0899/0814.Binary%20Tree%20Pruning/images/1028_1.png" style="width: 500px; height: 115px;" />
<pre>
<strong>输入：</strong>root = [1,0,1,0,0,0,1]
<strong>输出：</strong>[1,null,1,null,1]
</pre>

<p><strong>示例 3：</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/0800-0899/0814.Binary%20Tree%20Pruning/images/1028.png" style="width: 500px; height: 134px;" />
<pre>
<strong>输入：</strong>root = [1,1,0,1,1,0,1,0]
<strong>输出：</strong>[1,1,0,1,1,null,1]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>树中节点的数目在范围 <code>[1, 200]</code> 内</li>
	<li><code>Node.val</code> 为 <code>0</code> 或 <code>1</code></li>
</ul>

## 解法

### 方法一：DFS

观察叶节点，当叶节点 `val` 为 0 时，便将该节点抹去。回溯，查看其父节点是否成为了新的叶节点，依照此规则自底向上。

<!-- tabs:start -->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def pruneTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root is None:
            return None
        root.left = self.pruneTree(root.left)
        root.right = self.pruneTree(root.right)
        if root.val == 0 and root.left is None and root.right is None:
            return None
        return root
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode pruneTree(TreeNode root) {
        if (root == null) {
            return null;
        }
        root.left = pruneTree(root.left);
        root.right = pruneTree(root.right);
        if (root.val == 0 && root.left == null && root.right == null) {
            return null;
        }
        return root;
    }
}
```

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* pruneTree(TreeNode* root) {
        if (!root) return nullptr;
        root->left = pruneTree(root->left);
        root->right = pruneTree(root->right);
        if (!root->val && !root->left && !root->right) return nullptr;
        return root;
    }
};
```

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func pruneTree(root *TreeNode) *TreeNode {
	if root == nil {
		return nil
	}
	root.Left = pruneTree(root.Left)
	root.Right = pruneTree(root.Right)
	if root.Val == 0 && root.Left == nil && root.Right == nil {
		return nil
	}
	return root
}
```

```ts
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | null
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */

function pruneTree(root: TreeNode | null): TreeNode | null {
    if (root == null) {
        return root;
    }
    root.left = pruneTree(root.left);
    root.right = pruneTree(root.right);
    if (root.val == 0 && root.left == null && root.right == null) {
        return null;
    }
    return root;
}
```

```rust
// Definition for a binary tree node.
// #[derive(Debug, PartialEq, Eq)]
// pub struct TreeNode {
//   pub val: i32,
//   pub left: Option<Rc<RefCell<TreeNode>>>,
//   pub right: Option<Rc<RefCell<TreeNode>>>,
// }
//
// impl TreeNode {
//   #[inline]
//   pub fn new(val: i32) -> Self {
//     TreeNode {
//       val,
//       left: None,
//       right: None
//     }
//   }
// }
use std::rc::Rc;
use std::cell::RefCell;
impl Solution {
    pub fn prune_tree(root: Option<Rc<RefCell<TreeNode>>>) -> Option<Rc<RefCell<TreeNode>>> {
        if root.is_none() {
            return None;
        }

        let root = root.unwrap();
        let left = Self::prune_tree(root.borrow_mut().left.take());
        let right = Self::prune_tree(root.borrow_mut().right.take());
        if root.borrow().val == 0 && left.is_none() && right.is_none() {
            return None;
        }

        root.borrow_mut().left = left;
        root.borrow_mut().right = right;
        Some(root)
    }
}
```

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
 * @return {TreeNode}
 */
var pruneTree = function (root) {
    if (!root) return null;
    root.left = pruneTree(root.left);
    root.right = pruneTree(root.right);
    if (root.val == 0 && !root.left && !root.right) {
        return null;
    }
    return root;
};
```

<!-- tabs:end -->

<!-- end -->
