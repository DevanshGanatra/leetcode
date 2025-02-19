---
comments: true
difficulty: 中等
edit_url: https://github.com/doocs/leetcode/edit/main/solution/2600-2699/2657.Find%20the%20Prefix%20Common%20Array%20of%20Two%20Arrays/README.md
rating: 1304
tags:
    - 位运算
    - 数组
    - 哈希表
---

# [2657. 找到两个数组的前缀公共数组](https://leetcode.cn/problems/find-the-prefix-common-array-of-two-arrays)

[English Version](/solution/2600-2699/2657.Find%20the%20Prefix%20Common%20Array%20of%20Two%20Arrays/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给你两个下标从 <strong>0</strong>&nbsp;开始长度为 <code>n</code>&nbsp;的整数排列&nbsp;<code>A</code> 和&nbsp;<code>B</code>&nbsp;。</p>

<p><code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;的 <strong>前缀公共数组</strong>&nbsp;定义为数组&nbsp;<code>C</code>&nbsp;，其中&nbsp;<code>C[i]</code>&nbsp;是数组&nbsp;<code>A</code> 和&nbsp;<code>B</code>&nbsp;到下标为&nbsp;<code>i</code>&nbsp;之前公共元素的数目。</p>

<p>请你返回 <code>A</code>&nbsp;和 <code>B</code>&nbsp;的 <strong>前缀公共数组</strong>&nbsp;。</p>

<p>如果一个长度为 <code>n</code>&nbsp;的数组包含 <code>1</code>&nbsp;到 <code>n</code>&nbsp;的元素恰好一次，我们称这个数组是一个长度为 <code>n</code>&nbsp;的 <strong>排列</strong>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>A = [1,3,2,4], B = [3,1,2,4]
<b>输出：</b>[0,2,3,4]
<b>解释：</b>i = 0：没有公共元素，所以 C[0] = 0 。
i = 1：1 和 3 是两个数组的前缀公共元素，所以 C[1] = 2 。
i = 2：1，2 和 3 是两个数组的前缀公共元素，所以 C[2] = 3 。
i = 3：1，2，3 和 4 是两个数组的前缀公共元素，所以 C[3] = 4 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>A = [2,3,1], B = [3,1,2]
<b>输出：</b>[0,1,3]
<b>解释：</b>i = 0：没有公共元素，所以 C[0] = 0 。
i = 1：只有 3 是公共元素，所以 C[1] = 1 。
i = 2：1，2 和 3 是两个数组的前缀公共元素，所以 C[2] = 3 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= A.length == B.length == n &lt;= 50</code></li>
	<li><code>1 &lt;= A[i], B[i] &lt;= n</code></li>
	<li>题目保证&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;两个数组都是&nbsp;<code>n</code>&nbsp;个元素的排列。</li>
</ul>

## 解法

### 方法一：计数

我们可以使用两个数组 $cnt1$ 和 $cnt2$ 分别记录数组 $A$ 和 $B$ 中每个元素出现的次数，用数组 $ans$ 记录答案。

遍历数组 $A$ 和 $B$，将 $A[i]$ 在 $cnt1$ 中出现次数加一，将 $B[i]$ 在 $cnt2$ 中出现次数加一。然后枚举 $j \in [1,n]$，计算 $cnt1$ 和 $cnt2$ 中每个元素 $j$ 出现次数的最小值，累加到 $ans[i]$ 中。

遍历结束后，返回答案数组 $ans$ 即可。

时间复杂度 $O(n^2)$，空间复杂度 $O(n)$。其中 $n$ 是数组 $A$ 和 $B$ 的长度。

<!-- tabs:start -->

```python
class Solution:
    def findThePrefixCommonArray(self, A: List[int], B: List[int]) -> List[int]:
        ans = []
        cnt1 = Counter()
        cnt2 = Counter()
        for a, b in zip(A, B):
            cnt1[a] += 1
            cnt2[b] += 1
            t = sum(min(v, cnt2[x]) for x, v in cnt1.items())
            ans.append(t)
        return ans
```

```java
class Solution {
    public int[] findThePrefixCommonArray(int[] A, int[] B) {
        int n = A.length;
        int[] ans = new int[n];
        int[] cnt1 = new int[n + 1];
        int[] cnt2 = new int[n + 1];
        for (int i = 0; i < n; ++i) {
            ++cnt1[A[i]];
            ++cnt2[B[i]];
            for (int j = 1; j <= n; ++j) {
                ans[i] += Math.min(cnt1[j], cnt2[j]);
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B) {
        int n = A.size();
        vector<int> ans(n);
        vector<int> cnt1(n + 1), cnt2(n + 1);
        for (int i = 0; i < n; ++i) {
            ++cnt1[A[i]];
            ++cnt2[B[i]];
            for (int j = 1; j <= n; ++j) {
                ans[i] += min(cnt1[j], cnt2[j]);
            }
        }
        return ans;
    }
};
```

```go
func findThePrefixCommonArray(A []int, B []int) []int {
	n := len(A)
	cnt1 := make([]int, n+1)
	cnt2 := make([]int, n+1)
	ans := make([]int, n)
	for i, a := range A {
		b := B[i]
		cnt1[a]++
		cnt2[b]++
		for j := 1; j <= n; j++ {
			ans[i] += min(cnt1[j], cnt2[j])
		}
	}
	return ans
}
```

```ts
function findThePrefixCommonArray(A: number[], B: number[]): number[] {
    const n = A.length;
    const cnt1: number[] = Array(n + 1).fill(0);
    const cnt2: number[] = Array(n + 1).fill(0);
    const ans: number[] = Array(n).fill(0);
    for (let i = 0; i < n; ++i) {
        ++cnt1[A[i]];
        ++cnt2[B[i]];
        for (let j = 1; j <= n; ++j) {
            ans[i] += Math.min(cnt1[j], cnt2[j]);
        }
    }
    return ans;
}
```

<!-- tabs:end -->

### 方法二：位运算（异或运算）

我们可以使用一个长度为 $n+1$ 的数组 $vis$ 记录数组 $A$ 和 $B$ 中每个元素的出现情况，数组 $vis$ 的初始值为 $1$。另外，我们用一个变量 $s$ 记录当前公共元素的个数。

接下来，我们遍历数组 $A$ 和 $B$，更新 $vis[A[i]] = vis[A[i]] \oplus 1$，并且更新 $vis[B[i]] = vis[B[i]] \oplus 1$，其中 $\oplus$ 表示异或运算。

如果遍历到当前位置，元素 $A[i]$ 出现过两次（即在数组 $A$ 和 $B$ 中都出现过），那么 $vis[A[i]]$ 的值将为会 $1$，我们将 $s$ 加一。同理，如果元素 $B[i]$ 出现过两次，那么 $vis[B[i]]$ 的值将为会 $1$，我们将 $s$ 加一。然后将 $s$ 的值加入到答案数组 $ans$ 中。

遍历结束后，返回答案数组 $ans$ 即可。

时间复杂度 $O(n)$，空间复杂度 $O(n)$。其中 $n$ 是数组 $A$ 和 $B$ 的长度。

<!-- tabs:start -->

```python
class Solution:
    def findThePrefixCommonArray(self, A: List[int], B: List[int]) -> List[int]:
        ans = []
        vis = [1] * (len(A) + 1)
        s = 0
        for a, b in zip(A, B):
            vis[a] ^= 1
            s += vis[a]
            vis[b] ^= 1
            s += vis[b]
            ans.append(s)
        return ans
```

```java
class Solution {
    public int[] findThePrefixCommonArray(int[] A, int[] B) {
        int n = A.length;
        int[] ans = new int[n];
        int[] vis = new int[n + 1];
        Arrays.fill(vis, 1);
        int s = 0;
        for (int i = 0; i < n; ++i) {
            vis[A[i]] ^= 1;
            s += vis[A[i]];
            vis[B[i]] ^= 1;
            s += vis[B[i]];
            ans[i] = s;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B) {
        int n = A.size();
        vector<int> ans;
        vector<int> vis(n + 1, 1);
        int s = 0;
        for (int i = 0; i < n; ++i) {
            vis[A[i]] ^= 1;
            s += vis[A[i]];
            vis[B[i]] ^= 1;
            s += vis[B[i]];
            ans.push_back(s);
        }
        return ans;
    }
};
```

```go
func findThePrefixCommonArray(A []int, B []int) (ans []int) {
	vis := make([]int, len(A)+1)
	for i := range vis {
		vis[i] = 1
	}
	s := 0
	for i, a := range A {
		b := B[i]
		vis[a] ^= 1
		s += vis[a]
		vis[b] ^= 1
		s += vis[b]
		ans = append(ans, s)
	}
	return
}
```

```ts
function findThePrefixCommonArray(A: number[], B: number[]): number[] {
    const n = A.length;
    const vis: number[] = Array(n + 1).fill(1);
    const ans: number[] = [];
    let s = 0;
    for (let i = 0; i < n; ++i) {
        const [a, b] = [A[i], B[i]];
        vis[a] ^= 1;
        s += vis[a];
        vis[b] ^= 1;
        s += vis[b];
        ans.push(s);
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
