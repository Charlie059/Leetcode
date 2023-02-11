
# 1806. Minimum Number of Operations to Reinitialize a Permutation - 还原排列的最少操作步数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Simulation-模拟-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an <strong>even</strong> integer <code>n</code>​​​​​​. You initially have a permutation <code>perm</code> of size <code>n</code>​​ where <code>perm[i] == i</code>​ <strong>(0-indexed)</strong>​​​​.</p>

<p>In one operation, you will create a new array <code>arr</code>, and for each <code>i</code>:</p>

<ul>
	<li>If <code>i % 2 == 0</code>, then <code>arr[i] = perm[i / 2]</code>.</li>
	<li>If <code>i % 2 == 1</code>, then <code>arr[i] = perm[n / 2 + (i - 1) / 2]</code>.</li>
</ul>

<p>You will then assign <code>arr</code>​​​​ to <code>perm</code>.</p>

<p>Return <em>the minimum <strong>non-zero</strong> number of operations you need to perform on </em><code>perm</code><em> to return the permutation to its initial value.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 2
<strong>Output:</strong> 1
<strong>Explanation:</strong> perm = [0,1] initially.
After the 1<sup>st</sup> operation, perm = [0,1]
So it takes only 1 operation.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 4
<strong>Output:</strong> 2
<strong>Explanation:</strong> perm = [0,1,2,3] initially.
After the 1<sup>st</sup> operation, perm = [0,2,1,3]
After the 2<sup>nd</sup> operation, perm = [0,1,2,3]
So it takes only 2 operations.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 6
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= n &lt;= 1000</code></li>
	<li><code>n</code>​​​​​​ is even.</li>
</ul>


### ZH-CN:
<p>给你一个偶数 <code>n</code>​​​​​​ ，已知存在一个长度为 <code>n</code> 的排列 <code>perm</code> ，其中 <code>perm[i] == i</code>​（下标 <strong>从 0 开始</strong> 计数）。</p>

<p>一步操作中，你将创建一个新数组 <code>arr</code> ，对于每个 <code>i</code> ：</p>

<ul>
	<li>如果 <code>i % 2 == 0</code> ，那么 <code>arr[i] = perm[i / 2]</code></li>
	<li>如果 <code>i % 2 == 1</code> ，那么 <code>arr[i] = perm[n / 2 + (i - 1) / 2]</code></li>
</ul>

<p>然后将 <code>arr</code>​​ 赋值​​给 <code>perm</code> 。</p>

<p>要想使 <code>perm</code> 回到排列初始值，至少需要执行多少步操作？返回最小的 <strong>非零</strong> 操作步数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 2
<strong>输出：</strong>1
<strong>解释：</strong>最初，perm = [0,1]
第 1 步操作后，perm = [0,1]
所以，仅需执行 1 步操作</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 4
<strong>输出：</strong>2
<strong>解释：</strong>最初，perm = [0,1,2,3]
第 1 步操作后，perm = [0,2,1,3]
第 2 步操作后，perm = [0,1,2,3]
所以，仅需执行 2 步操作</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 6
<strong>输出：</strong>4
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 <= n <= 1000</code></li>
	<li><code>n</code>​​​​​​ 是一个偶数</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimum-number-of-operations-to-reinitialize-a-permutation/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/minimum-number-of-operations-to-reinitialize-a-permutation/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 32 ms | 25 MB | 2023/01/08 15:32 |

```cpp

class Solution {
public:
    int reinitializePermutation(int n) {
        vector<int> perm(n, 0);
        for(int i = 0; i < n; i++){
            perm[i] = i;
        }

        int ans = 0;
        
        while(true){
            ans++;

            bool isChanged = false;
            vector<int> arr = perm;
            for(int i = 0; i < n; i++){
                if(i % 2 == 0) arr[i] = perm[i / 2];
                else arr[i] = perm[n / 2 + (i - 1) / 2];
                if(i != arr[i]) isChanged = true;
            }

            if(!isChanged) break;
            perm = arr;
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

