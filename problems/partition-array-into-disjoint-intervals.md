
# 915. Partition Array into Disjoint Intervals - 分割数组

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer array <code>nums</code>, partition it into two (contiguous) subarrays <code>left</code> and <code>right</code> so that:</p>

<ul>
	<li>Every element in <code>left</code> is less than or equal to every element in <code>right</code>.</li>
	<li><code>left</code> and <code>right</code> are non-empty.</li>
	<li><code>left</code> has the smallest possible size.</li>
</ul>

<p>Return <em>the length of </em><code>left</code><em> after such a partitioning</em>.</p>

<p>Test cases are generated such that partitioning exists.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,0,3,8,6]
<strong>Output:</strong> 3
<strong>Explanation:</strong> left = [5,0,3], right = [8,6]
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,1,0,6,12]
<strong>Output:</strong> 4
<strong>Explanation:</strong> left = [1,1,1,0], right = [6,12]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li>There is at least one valid answer for the given input.</li>
</ul>


### ZH-CN:
<p>给定一个数组&nbsp;<code>nums</code>&nbsp;，将其划分为两个连续子数组&nbsp;<code>left</code>&nbsp;和&nbsp;<code>right</code>，&nbsp;使得：</p>

<ul>
	<li><code>left</code>&nbsp;中的每个元素都小于或等于&nbsp;<code>right</code>&nbsp;中的每个元素。</li>
	<li><code>left</code> 和&nbsp;<code>right</code>&nbsp;都是非空的。</li>
	<li><code>left</code> 的长度要尽可能小。</li>
</ul>

<p><em>在完成这样的分组后返回&nbsp;<code>left</code>&nbsp;的&nbsp;<strong>长度&nbsp;</strong></em>。</p>

<p>用例可以保证存在这样的划分方法。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [5,0,3,8,6]
<strong>输出：</strong>3
<strong>解释：</strong>left = [5,0,3]，right = [8,6]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,1,1,0,6,12]
<strong>输出：</strong>4
<strong>解释：</strong>left = [1,1,1,0]，right = [6,12]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li>可以保证至少有一种方法能够按题目所描述的那样对 <code>nums</code> 进行划分。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/partition-array-into-disjoint-intervals/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/partition-array-into-disjoint-intervals/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 164 ms | 99.8 MB | 2022/10/23 23:23 |

```cpp

class Solution {
public:
    int partitionDisjoint(vector<int>& nums) {
        // [1,1,1,0,6,12]
        // [1,1,1,1,6,12]
        // [0,0,0,0,6,12]

        // [5,0,3,8,6]
        // [5,5,5,8,8]
        // [0,0,3,6,6]

        const int n = nums.size();
        vector<int> l2r(n, 0), r2l(n, 0);

        int currMax = nums[0];
        int currMin = nums[n - 1];
        for(int i = 0; i < n; i++){
            currMax = max(currMax, nums[i]);
            l2r[i] = currMax;
            currMin = min(currMin, nums[n - i - 1]);
            r2l[n - i - 1] = currMin;
        }

        int ans = 1;
        for(int i = 0; i < n - 1; i++){
            int currMax = l2r[i];
            int currMin = r2l[i + 1];
            if(currMax <= currMin) break;
            else ans++;
        }
        
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

