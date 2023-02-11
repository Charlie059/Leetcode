
# 698. Partition to K Equal Sum Subsets - 划分为k个相等的子集

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Bit Manipulation-位运算-blue.svg">   <img src="https://img.shields.io/badge/Memoization-记忆化搜索-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Backtracking-回溯-blue.svg">   <img src="https://img.shields.io/badge/Bitmask-状态压缩-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <code>true</code> if it is possible to divide this array into <code>k</code> non-empty subsets whose sums are all equal.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,3,2,3,5,2,1], k = 4
<strong>Output:</strong> true
<strong>Explanation:</strong> It is possible to divide it into 4 subsets (5), (1, 4), (2,3), (2,3) with equal sums.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4], k = 3
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 16</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li>The frequency of each element is in the range <code>[1, 4]</code>.</li>
</ul>


### ZH-CN:
<p>给定一个整数数组&nbsp;&nbsp;<code>nums</code> 和一个正整数 <code>k</code>，找出是否有可能把这个数组分成 <code>k</code> 个非空子集，其总和都相等。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong> nums = [4, 3, 2, 3, 5, 2, 1], k = 4
<strong>输出：</strong> True
<strong>说明：</strong> 有可能将其分成 4 个子集（5），（1,4），（2,3），（2,3）等于总和。</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,2,3,4], k = 3
<strong>输出:</strong> false</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= len(nums) &lt;= 16</code></li>
	<li><code>0 &lt; nums[i] &lt; 10000</code></li>
	<li>每个元素的频率在 <code>[1,4]</code> 范围内</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/partition-to-k-equal-sum-subsets/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 9.3 MB | 2022/12/13 0:10 |

```cpp

class Solution {
public:
    vector<int> sums;
    int t;

    bool dfs(vector<int>& nums, int currIdx, const int k){
        if(currIdx == nums.size()) return true;
        int curr = nums[currIdx];
        for(int j = 0; j < k; j++){
            if (j > 0 && sums[j] == sums[j - 1]) continue; //?
            if(sums[j] + curr > t) continue;
            sums[j] += curr;
            if(dfs(nums, currIdx + 1, k)) return true;
            sums[j] -= curr;
        }
        return false;
    }
    bool canPartitionKSubsets(vector<int>& nums, int k) {
        const int n = nums.size();
        int sum = accumulate(nums.begin(), nums.end(), 0);
        if(sum % k != 0) return false;
        sort(nums.rbegin(), nums.rend());
        t = sum / k;
        sums.resize(k);
        return dfs(nums, 0, k);
    }
};

```
## My Notes - 我的笔记


No notes

