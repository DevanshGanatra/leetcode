---
comments: true
edit_url: https://github.com/doocs/leetcode/edit/main/lcp/LCP%2001.%20%E7%8C%9C%E6%95%B0%E5%AD%97/README.md
---

# [LCP 01. 猜数字](https://leetcode.cn/problems/guess-numbers)

## 题目描述

<!-- 这里写题目描述 -->

<p>小A 和 小B 在玩猜数字。小B 每次从 1, 2, 3 中随机选择一个，小A 每次也从 1, 2, 3 中选择一个猜。他们一共进行三次这个游戏，请返回 小A 猜对了几次？</p>

<p>输入的<code>guess</code>数组为 小A 每次的猜测，<code>answer</code>数组为 小B 每次的选择。<code>guess</code>和<code>answer</code>的长度都等于3。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>guess = [1,2,3], answer = [1,2,3]
<strong>输出：</strong>3
<strong>解释：</strong>小A 每次都猜对了。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>guess = [2,2,3], answer = [3,2,1]
<strong>输出：</strong>1
<strong>解释：</strong>小A 只猜对了第二次。</pre>

<p> </p>

<p><strong>限制：</strong></p>

<ol>
	<li><code>guess</code> 的长度 = 3</li>
	<li><code>answer</code> 的长度 = 3</li>
	<li><code>guess</code> 的元素取值为 <code>{1, 2, 3}</code> 之一。</li>
	<li><code>answer</code> 的元素取值为 <code>{1, 2, 3}</code> 之一。</li>
</ol>

## 解法

### 方法一：遍历

我们同时遍历两个数组，如果对应位置的元素相等，那么答案加一。

时间复杂度 $O(n)$，其中 $n$ 是数组的长度，本题中 $n=3$。空间复杂度 $O(1)$。

<!-- tabs:start -->

```python
class Solution:
    def game(self, guess: List[int], answer: List[int]) -> int:
        return sum(a == b for a, b in zip(guess, answer))
```

```java
class Solution {
    public int game(int[] guess, int[] answer) {
        int ans = 0;
        for (int i = 0; i < 3; ++i) {
            if (guess[i] == answer[i]) {
                ++ans;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int game(vector<int>& guess, vector<int>& answer) {
        int ans = 0;
        for (int i = 0; i < 3; ++i) {
            ans += guess[i] == answer[i];
        }
        return ans;
    }
};
```

```go
func game(guess []int, answer []int) (ans int) {
	for i, a := range guess {
		if a == answer[i] {
			ans++
		}
	}
	return
}
```

```ts
function game(guess: number[], answer: number[]): number {
    let ans = 0;
    for (let i = 0; i < 3; ++i) {
        if (guess[i] === answer[i]) {
            ++ans;
        }
    }
    return ans;
}
```

```js
/**
 * @param {number[]} guess
 * @param {number[]} answer
 * @return {number}
 */
var game = function (guess, answer) {
    let ans = 0;
    for (let i = 0; i < 3; ++i) {
        if (guess[i] === answer[i]) {
            ++ans;
        }
    }
    return ans;
};
```

```c
int game(int* guess, int guessSize, int* answer, int answerSize) {
    int res = 0;
    for (int i = 0; i < 3; i++) {
        if (guess[i] == answer[i]) {
            res++;
        }
    }
    return res;
}
```

<!-- tabs:end -->

### 方法二

<!-- tabs:start -->

```ts
function game(guess: number[], answer: number[]): number {
    return guess.reduce((acc, cur, index) => (cur === answer[index] ? acc + 1 : acc), 0);
}
```

<!-- tabs:end -->

<!-- end -->
