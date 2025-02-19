---
comments: true
difficulty: 困难
edit_url: https://github.com/doocs/leetcode/edit/main/lcp/LCP%2060.%20%E5%8A%9B%E6%89%A3%E6%B3%A1%E6%B3%A1%E9%BE%99/README.md
---

# [LCP 60. 力扣泡泡龙](https://leetcode.cn/problems/WInSav)

## 题目描述

<!-- 这里写题目描述 -->

欢迎各位勇者来到力扣城，本次试炼主题为「力扣泡泡龙」。

游戏初始状态的泡泡形如二叉树 `root`，每个节点值对应了该泡泡的分值。勇者最多可以击破一个节点泡泡，要求满足：

-   被击破的节点泡泡 **至多** 只有一个子节点泡泡
-   当被击破的节点泡泡有子节点泡泡时，则子节点泡泡将取代被击破泡泡的位置
    > 注：即整棵子树泡泡上移

请问在击破一个节点泡泡操作或无击破操作后，二叉泡泡树的最大「层和」是多少。

**注意：**

-   「层和」为同一高度的所有节点的分值之和

**示例 1：**

> 输入：`root = [6,0,3,null,8]`
>
> 输出：`11`
>
> 解释：勇者的最佳方案如图所示
> ![image.png](https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcp/LCP%2060.%20%E5%8A%9B%E6%89%A3%E6%B3%A1%E6%B3%A1%E9%BE%99/images/1648180809-XSWPLu-image.png){:height="100px"}

**示例 2：**

> 输入：`root = [5,6,2,4,null,null,1,3,5]`
>
> 输出：`9`
>
> 解释：勇者击破 6 节点，此时「层和」最大为 3+5+1 = 9
> ![image.png](https://fastly.jsdelivr.net/gh/doocs/leetcode@main/lcp/LCP%2060.%20%E5%8A%9B%E6%89%A3%E6%B3%A1%E6%B3%A1%E9%BE%99/images/1648180769-TLpYop-image.png){:height="200px"}

**示例 3：**

> 输入：`root = [-5,1,7]`
>
> 输出：`8`
>
> 解释：勇者不击破节点，「层和」最大为 1+7 = 8

**提示**：

-   `2 <= 树中节点个数 <= 10^5`
-   `-10000 <= 树中节点的值 <= 10000`

## 解法

<!-- end -->
