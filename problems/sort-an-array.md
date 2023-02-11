
# 912. Sort an Array - 排序数组

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Divide and Conquer-分治-blue.svg">   <img src="https://img.shields.io/badge/Bucket Sort-桶排序-blue.svg">   <img src="https://img.shields.io/badge/Counting Sort-计数排序-blue.svg">   <img src="https://img.shields.io/badge/Radix Sort-基数排序-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">   <img src="https://img.shields.io/badge/Heap (Priority Queue)-堆（优先队列）-blue.svg">   <img src="https://img.shields.io/badge/Merge Sort-归并排序-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an array of integers <code>nums</code>, sort the array in ascending order and return it.</p>

<p>You must solve the problem <strong>without using any built-in</strong> functions in <code>O(nlog(n))</code> time complexity and with the smallest space complexity possible.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,2,3,1]
<strong>Output:</strong> [1,2,3,5]
<strong>Explanation:</strong> After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,1,1,2,0,0]
<strong>Output:</strong> [0,0,1,1,2,5]
<strong>Explanation:</strong> Note that the values of nums are not necessairly unique.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-5 * 10<sup>4</sup> &lt;= nums[i] &lt;= 5 * 10<sup>4</sup></code></li>
</ul>


### ZH-CN:
<p>给你一个整数数组&nbsp;<code>nums</code>，请你将该数组升序排列。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [5,2,3,1]
<strong>输出：</strong>[1,2,3,5]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [5,1,1,2,0,0]
<strong>输出：</strong>[0,0,1,1,2,5]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-5 * 10<sup>4</sup> &lt;= nums[i] &lt;= 5 * 10<sup>4</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/sort-an-array/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/sort-an-array/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 176 ms | 57.7 MB | 2022/12/25 1:18 |

```cpp

class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        vector<int> t(nums.size());
        function<void(int, int)> mergeSort = [&](int l, int r) {
            if (l + 1 >= r) return;
            int m = l + (r - l) / 2;
            mergeSort(l, m);
            mergeSort(m, r);
            int i1 = l;
            int i2 = m;
            int index = 0;
            while (i1 < m || i2 < r)
                if (i2 == r) t[index++] = nums[i1++];
                else if(i1 == m) t[index++] = nums[i2++];
                else if(nums[i1] < nums[i2]) t[index++] = nums[i1++];
                else t[index++] = nums[i2++];      
                // if (i2 == r || (i1 < m && nums[i1] < nums[i2])) t[index++] = nums[i1++];
                // else t[index++] = nums[i2++];      
            std::copy(begin(t), begin(t) + index, begin(nums) + l);
        };
        
        mergeSort(0, nums.size());
        return nums;
    }
};

```
## My Notes - 我的笔记


No notes

