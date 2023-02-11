
# 2411. Smallest Subarrays With Maximum Bitwise OR - 按位或最大的最小子数组长度

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Bit Manipulation-位运算-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Binary Search-二分查找-blue.svg">   <img src="https://img.shields.io/badge/Sliding Window-滑动窗口-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a <strong>0-indexed</strong> array <code>nums</code> of length <code>n</code>, consisting of non-negative integers. For each index <code>i</code> from <code>0</code> to <code>n - 1</code>, you must determine the size of the <strong>minimum sized</strong> non-empty subarray of <code>nums</code> starting at <code>i</code> (<strong>inclusive</strong>) that has the <strong>maximum</strong> possible <strong>bitwise OR</strong>.</p>

<ul>
	<li>In other words, let <code>B<sub>ij</sub></code> be the bitwise OR of the subarray <code>nums[i...j]</code>. You need to find the smallest subarray starting at <code>i</code>, such that bitwise OR of this subarray is equal to <code>max(B<sub>ik</sub>)</code> where <code>i &lt;= k &lt;= n - 1</code>.</li>
</ul>

<p>The bitwise OR of an array is the bitwise OR of all the numbers in it.</p>

<p>Return <em>an integer array </em><code>answer</code><em> of size </em><code>n</code><em> where </em><code>answer[i]</code><em> is the length of the <strong>minimum</strong> sized subarray starting at </em><code>i</code><em> with <strong>maximum</strong> bitwise OR.</em></p>

<p>A <strong>subarray</strong> is a contiguous non-empty sequence of elements within an array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,0,2,1,3]
<strong>Output:</strong> [3,3,2,2,1]
<strong>Explanation:</strong>
The maximum possible bitwise OR starting at any index is 3. 
- Starting at index 0, the shortest subarray that yields it is [1,0,2].
- Starting at index 1, the shortest subarray that yields the maximum bitwise OR is [0,2,1].
- Starting at index 2, the shortest subarray that yields the maximum bitwise OR is [2,1].
- Starting at index 3, the shortest subarray that yields the maximum bitwise OR is [1,3].
- Starting at index 4, the shortest subarray that yields the maximum bitwise OR is [3].
Therefore, we return [3,3,2,2,1]. 
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2]
<strong>Output:</strong> [2,1]
<strong>Explanation:
</strong>Starting at index 0, the shortest subarray that yields the maximum bitwise OR is of length 2.
Starting at index 1, the shortest subarray that yields the maximum bitwise OR is of length 1.
Therefore, we return [2,1].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>


### ZH-CN:
<p>给你一个长度为 <code>n</code>&nbsp;下标从 <strong>0</strong>&nbsp;开始的数组&nbsp;<code>nums</code>&nbsp;，数组中所有数字均为非负整数。对于&nbsp;<code>0</code>&nbsp;到&nbsp;<code>n - 1</code>&nbsp;之间的每一个下标 <code>i</code>&nbsp;，你需要找出&nbsp;<code>nums</code>&nbsp;中一个 <strong>最小</strong> 非空子数组，它的起始位置为&nbsp;<code>i</code>&nbsp;（包含这个位置），同时有&nbsp;<strong>最大</strong>&nbsp;的 <strong>按位或</strong><b>运算值</b>&nbsp;。</p>

<ul>
	<li>换言之，令&nbsp;<code>B<sub>ij</sub></code>&nbsp;表示子数组&nbsp;<code>nums[i...j]</code>&nbsp;的按位或运算的结果，你需要找到一个起始位置为&nbsp;<code>i</code>&nbsp;的最小子数组，这个子数组的按位或运算的结果等于&nbsp;<code>max(B<sub>ik</sub>)</code>&nbsp;，其中&nbsp;<code>i &lt;= k &lt;= n - 1</code>&nbsp;。</li>
</ul>

<p>一个数组的按位或运算值是这个数组里所有数字按位或运算的结果。</p>

<p>请你返回一个大小为 <code>n</code>&nbsp;的整数数组<em>&nbsp;</em><code>answer</code>，其中<em>&nbsp;</em><code>answer[i]</code>是开始位置为&nbsp;<code>i</code>&nbsp;，按位或运算结果最大，且&nbsp;<strong>最短</strong>&nbsp;子数组的长度。</p>

<p><strong>子数组</strong>&nbsp;是数组里一段连续非空元素组成的序列。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>nums = [1,0,2,1,3]
<b>输出：</b>[3,3,2,2,1]
<strong>解释：</strong>
任何位置开始，最大按位或运算的结果都是 3 。
- 下标 0 处，能得到结果 3 的最短子数组是 [1,0,2] 。
- 下标 1 处，能得到结果 3 的最短子数组是 [0,2,1] 。
- 下标 2 处，能得到结果 3 的最短子数组是 [2,1] 。
- 下标 3 处，能得到结果 3 的最短子数组是 [1,3] 。
- 下标 4 处，能得到结果 3 的最短子数组是 [3] 。
所以我们返回 [3,3,2,2,1] 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums = [1,2]
<b>输出：</b>[2,1]
<strong>解释：
</strong>下标 0 处，能得到最大按位或运算值的最短子数组长度为 2 。
下标 1 处，能得到最大按位或运算值的最短子数组长度为 1 。
所以我们返回 [2,1] 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/smallest-subarrays-with-maximum-bitwise-or/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/smallest-subarrays-with-maximum-bitwise-or/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 140 ms | 54.6 MB | 2022/09/17 16:24 |

```cpp

class Solution {
public:
    vector<int> smallestSubarrays(vector<int>& nums) {
        const int n = nums.size();
        vector<int> flag(32, - 1);
        vector<int> ans(n, -1);

        for(int i = n - 1; i >= 0; i--){
            int tmp = 1;
            for(int j = 0; j < 32; j++){
                if((nums[i] >> j) & 1){
                    flag[j] = i;
                }else if(flag[j] != -1){
                    tmp = max(tmp, flag[j] - i + 1);
                }
            }
            ans[i] = tmp;
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

