
# 2420. Find All Good Indices - 找到所有好下标

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Prefix Sum-前缀和-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> of size <code>n</code> and a positive integer <code>k</code>.</p>

<p>We call an index <code>i</code> in the range <code>k &lt;= i &lt; n - k</code> <strong>good</strong> if the following conditions are satisfied:</p>

<ul>
	<li>The <code>k</code> elements that are just <strong>before</strong> the index <code>i</code> are in <strong>non-increasing</strong> order.</li>
	<li>The <code>k</code> elements that are just <strong>after</strong> the index <code>i</code> are in <strong>non-decreasing</strong> order.</li>
</ul>

<p>Return <em>an array of all good indices sorted in <strong>increasing</strong> order</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,1,1,3,4,1], k = 2
<strong>Output:</strong> [2,3]
<strong>Explanation:</strong> There are two good indices in the array:
- Index 2. The subarray [2,1] is in non-increasing order, and the subarray [1,3] is in non-decreasing order.
- Index 3. The subarray [1,1] is in non-increasing order, and the subarray [3,4] is in non-decreasing order.
Note that the index 4 is not good because [4,1] is not non-decreasing.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,1,2], k = 2
<strong>Output:</strong> []
<strong>Explanation:</strong> There are no good indices in this array.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>3 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= k &lt;= n / 2</code></li>
</ul>


### ZH-CN:
<p>给你一个大小为 <code>n</code>&nbsp;下标从 <strong>0</strong>&nbsp;开始的整数数组&nbsp;<code>nums</code>&nbsp;和一个正整数&nbsp;<code>k</code>&nbsp;。</p>

<p>对于&nbsp;<code>k &lt;= i &lt; n - k</code>&nbsp;之间的一个下标&nbsp;<code>i</code>&nbsp;，如果它满足以下条件，我们就称它为一个&nbsp;<strong>好</strong>&nbsp;下标：</p>

<ul>
	<li>下标 <code>i</code> <strong>之前</strong> 的 <code>k</code>&nbsp;个元素是 <strong>非递增的</strong>&nbsp;。</li>
	<li>下标 <code>i</code> <strong>之后</strong>&nbsp;的 <code>k</code>&nbsp;个元素是 <strong>非递减的</strong>&nbsp;。</li>
</ul>

<p>按 <strong>升序</strong>&nbsp;返回所有好下标。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>nums = [2,1,1,1,3,4,1], k = 2
<b>输出：</b>[2,3]
<b>解释：</b>数组中有两个好下标：
- 下标 2 。子数组 [2,1] 是非递增的，子数组 [1,3] 是非递减的。
- 下标 3 。子数组 [1,1] 是非递增的，子数组 [3,4] 是非递减的。
注意，下标 4 不是好下标，因为 [4,1] 不是非递减的。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>nums = [2,1,1,2], k = 2
<b>输出：</b>[]
<b>解释：</b>数组中没有好下标。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>3 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= k &lt;= n / 2</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/find-all-good-indices/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/find-all-good-indices/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 120 ms | 86.8 MB | 2022/09/25 0:55 |

```cpp

class Solution {
public:
    vector<int> goodIndices(vector<int>& nums, int k) {
        const int n = nums.size();
        vector<int> f(n), g(n);
        f[0] = 1, g[n - 1] = 1;
        
        for(int i = 1; i < n; i++){
            if(nums[i] <= nums[i - 1]) f[i] = f[i - 1] + 1;
            else f[i] = 1;
        }

        for(int i = n - 2; i >= 0; i--){
            if(nums[i] <= nums[i + 1]) g[i] = g[i + 1] + 1;
            else g[i] = 1;
        }

        vector<int> ans;
        for(int i = k; i < n - k; i++){
            if(f[i - 1] >= k && g[i + 1] >= k) ans.push_back(i);
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

