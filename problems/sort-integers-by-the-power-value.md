
# 1387. Sort Integers by The Power Value - 将整数按权重排序

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Memoization-记忆化搜索-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">  


## Description - 题目描述

### EN:
<p>The power of an integer <code>x</code> is defined as the number of steps needed to transform <code>x</code> into <code>1</code> using the following steps:</p>

<ul>
	<li>if <code>x</code> is even then <code>x = x / 2</code></li>
	<li>if <code>x</code> is odd then <code>x = 3 * x + 1</code></li>
</ul>

<p>For example, the power of <code>x = 3</code> is <code>7</code> because <code>3</code> needs <code>7</code> steps to become <code>1</code> (<code>3 --&gt; 10 --&gt; 5 --&gt; 16 --&gt; 8 --&gt; 4 --&gt; 2 --&gt; 1</code>).</p>

<p>Given three integers <code>lo</code>, <code>hi</code> and <code>k</code>. The task is to sort all integers in the interval <code>[lo, hi]</code> by the power value in <strong>ascending order</strong>, if two or more integers have <strong>the same</strong> power value sort them by <strong>ascending order</strong>.</p>

<p>Return the <code>k<sup>th</sup></code> integer in the range <code>[lo, hi]</code> sorted by the power value.</p>

<p>Notice that for any integer <code>x</code> <code>(lo &lt;= x &lt;= hi)</code> it is <strong>guaranteed</strong> that <code>x</code> will transform into <code>1</code> using these steps and that the power of <code>x</code> is will <strong>fit</strong> in a 32-bit signed integer.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> lo = 12, hi = 15, k = 2
<strong>Output:</strong> 13
<strong>Explanation:</strong> The power of 12 is 9 (12 --&gt; 6 --&gt; 3 --&gt; 10 --&gt; 5 --&gt; 16 --&gt; 8 --&gt; 4 --&gt; 2 --&gt; 1)
The power of 13 is 9
The power of 14 is 17
The power of 15 is 17
The interval sorted by the power value [12,13,14,15]. For k = 2 answer is the second element which is 13.
Notice that 12 and 13 have the same power value and we sorted them in ascending order. Same for 14 and 15.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> lo = 7, hi = 11, k = 4
<strong>Output:</strong> 7
<strong>Explanation:</strong> The power array corresponding to the interval [7, 8, 9, 10, 11] is [16, 3, 19, 6, 14].
The interval sorted by power is [8, 10, 11, 7, 9].
The fourth number in the sorted array is 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= lo &lt;= hi &lt;= 1000</code></li>
	<li><code>1 &lt;= k &lt;= hi - lo + 1</code></li>
</ul>


### ZH-CN:
<p>我们将整数 <code>x</code>&nbsp;的 <strong>权重</strong> 定义为按照下述规则将 <code>x</code>&nbsp;变成 <code>1</code>&nbsp;所需要的步数：</p>

<ul>
	<li>如果&nbsp;<code>x</code>&nbsp;是偶数，那么&nbsp;<code>x = x / 2</code></li>
	<li>如果&nbsp;<code>x</code>&nbsp;是奇数，那么&nbsp;<code>x = 3 * x + 1</code></li>
</ul>

<p>比方说，x=3 的权重为 7 。因为 3 需要 7 步变成 1 （3 --&gt; 10 --&gt; 5 --&gt; 16 --&gt; 8 --&gt; 4 --&gt; 2 --&gt; 1）。</p>

<p>给你三个整数&nbsp;<code>lo</code>，&nbsp;<code>hi</code> 和&nbsp;<code>k</code>&nbsp;。你的任务是将区间&nbsp;<code>[lo, hi]</code>&nbsp;之间的整数按照它们的权重&nbsp;<strong>升序排序&nbsp;</strong>，如果大于等于 2 个整数有&nbsp;<strong>相同</strong>&nbsp;的权重，那么按照数字自身的数值&nbsp;<strong>升序排序</strong>&nbsp;。</p>

<p>请你返回区间&nbsp;<code>[lo, hi]</code>&nbsp;之间的整数按权重排序后的第&nbsp;<code>k</code>&nbsp;个数。</p>

<p>注意，题目保证对于任意整数&nbsp;<code>x</code>&nbsp;<code>（lo &lt;= x &lt;= hi）</code>&nbsp;，它变成&nbsp;<code>1</code> 所需要的步数是一个 32 位有符号整数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>lo = 12, hi = 15, k = 2
<strong>输出：</strong>13
<strong>解释：</strong>12 的权重为 9（12 --&gt; 6 --&gt; 3 --&gt; 10 --&gt; 5 --&gt; 16 --&gt; 8 --&gt; 4 --&gt; 2 --&gt; 1）
13 的权重为 9
14 的权重为 17
15 的权重为 17
区间内的数按权重排序以后的结果为 [12,13,14,15] 。对于 k = 2 ，答案是第二个整数也就是 13 。
注意，12 和 13 有相同的权重，所以我们按照它们本身升序排序。14 和 15 同理。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>lo = 7, hi = 11, k = 4
<strong>输出：</strong>7
<strong>解释：</strong>区间内整数 [7, 8, 9, 10, 11] 对应的权重为 [16, 3, 19, 6, 14] 。
按权重排序后得到的结果为 [8, 10, 11, 7, 9] 。
排序后数组中第 4 个数字为 7 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= lo &lt;= hi &lt;= 1000</code></li>
	<li><code>1 &lt;= k &lt;= hi - lo + 1</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/sort-integers-by-the-power-value/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/sort-integers-by-the-power-value/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 260 ms | 48.2 MB | 2022/01/26 20:37 |

```cpp

class Solution {
    unordered_map<int, int> dp;

public:
unordered_map <int, int> f;

    int getF(int x) {
        if (f.find(x) != f.end()) return f[x];
        if (x == 1) return f[x] = 0;
        if (x & 1) return f[x] = getF(x * 3 + 1) + 1;
        else return f[x] = getF(x / 2) + 1;
    }

    int getKth(int lo, int hi, int k) {
        vector <int> v;
        for (int i = lo; i <= hi; ++i) v.push_back(i);
        sort(v.begin(), v.end(), [&] (int u, int v) {
            if (getF(u) != getF(v)) return getF(u) < getF(v);
            else return u < v;
        });
        return v[k - 1];
    }
};



```
## My Notes - 我的笔记


No notes

