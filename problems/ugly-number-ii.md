
# 264. Ugly Number II - 丑数 II

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Heap (Priority Queue)-堆（优先队列）-blue.svg">  


## Description - 题目描述

### EN:
<p>An <strong>ugly number</strong> is a positive integer whose prime factors are limited to <code>2</code>, <code>3</code>, and <code>5</code>.</p>

<p>Given an integer <code>n</code>, return <em>the</em> <code>n<sup>th</sup></code> <em><strong>ugly number</strong></em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 12
<strong>Explanation:</strong> [1, 2, 3, 4, 5, 6, 8, 9, 10, 12] is the sequence of the first 10 ugly numbers.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 1
<strong>Explanation:</strong> 1 has no prime factors, therefore all of its prime factors are limited to 2, 3, and 5.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 1690</code></li>
</ul>


### ZH-CN:
<p>给你一个整数 <code>n</code> ，请你找出并返回第 <code>n</code> 个 <strong>丑数</strong> 。</p>

<p><strong>丑数 </strong>就是只包含质因数 <code>2</code>、<code>3</code> 和/或 <code>5</code> 的正整数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 10
<strong>输出：</strong>12
<strong>解释：</strong>[1, 2, 3, 4, 5, 6, 8, 9, 10, 12] 是由前 10 个丑数组成的序列。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>1
<strong>解释：</strong>1 通常被视为丑数。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n <= 1690</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/ugly-number-ii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/ugly-number-ii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 100 ms | 29.9 MB | 2022/12/25 1:53 |

```cpp

class Solution {
public:
    int nthUglyNumber(int n) {
        if(n == 1) return 1;
        auto comp = [](const long long a, const long long b){
            return a > b;
        };
        priority_queue<long long, vector<long long>, decltype(comp)> pq(comp);
        unordered_set<long long> hs;
        pq.push(1);
        hs.emplace(1);

        long long ans = 0;
        while(n != 0){
            ans = pq.top(); pq.pop();
            if(!hs.count(ans * 2)){
                pq.push(ans * 2);
                hs.emplace(ans * 2);
            }
            if(!hs.count(ans * 3)){
                pq.push(ans * 3);
                hs.emplace(ans * 3);
            }
            if(!hs.count(ans * 5)){
                pq.push(ans * 5);
                hs.emplace(ans * 5);
            }
            n--;
        }

        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

