
# 479. Largest Palindrome Product - 最大回文数乘积

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer n, return <em>the <strong>largest palindromic integer</strong> that can be represented as the product of two <code>n</code>-digits integers</em>. Since the answer can be very large, return it <strong>modulo</strong> <code>1337</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 2
<strong>Output:</strong> 987
Explanation: 99 x 91 = 9009, 9009 % 1337 = 987
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>


### ZH-CN:
<p>给定一个整数 n ，返回 <em>可表示为两个 <code>n</code>&nbsp;位整数乘积的 <strong>最大回文整数</strong></em> 。因为答案可能非常大，所以返回它对 <code>1337</code> <strong>取余</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<b>输入：</b>n = 2
<b>输出：</b>987
<strong>解释：</strong>99 x 91 = 9009, 9009 % 1337 = 987
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入：</strong> n = 1
<strong>输出：</strong> 9
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/largest-palindrome-product/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/largest-palindrome-product/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 88 ms | 6 MB | 2022/07/28 23:25 |

```cpp

class Solution {
public:
    int largestPalindrome(int n) {
        if(n == 1) return 9;

        int upper = pow(10, n) - 1;

        for(int left = upper;; left--){
            long p = left;

            for(int x = left; x > 0; x /= 10){
                p = p * 10 + x % 10;
            }

            for(long x = upper; x * x >= p; x--){
                if(p % x == 0) return p % 1337;
            }
        }
        return -1;
    }
};

```
## My Notes - 我的笔记


No notes

