
# 167. Two Sum II - Input Array Is Sorted - 两数之和 II - 输入有序数组

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/Binary Search-二分查找-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a <strong>1-indexed</strong> array of integers <code>numbers</code> that is already <strong><em>sorted in non-decreasing order</em></strong>, find two numbers such that they add up to a specific <code>target</code> number. Let these two numbers be <code>numbers[index<sub>1</sub>]</code> and <code>numbers[index<sub>2</sub>]</code> where <code>1 &lt;= index<sub>1</sub> &lt; index<sub>2</sub> &lt;= numbers.length</code>.</p>

<p>Return<em> the indices of the two numbers, </em><code>index<sub>1</sub></code><em> and </em><code>index<sub>2</sub></code><em>, <strong>added by one</strong> as an integer array </em><code>[index<sub>1</sub>, index<sub>2</sub>]</code><em> of length 2.</em></p>

<p>The tests are generated such that there is <strong>exactly one solution</strong>. You <strong>may not</strong> use the same element twice.</p>

<p>Your solution must use only constant extra space.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> numbers = [<u>2</u>,<u>7</u>,11,15], target = 9
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The sum of 2 and 7 is 9. Therefore, index<sub>1</sub> = 1, index<sub>2</sub> = 2. We return [1, 2].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> numbers = [<u>2</u>,3,<u>4</u>], target = 6
<strong>Output:</strong> [1,3]
<strong>Explanation:</strong> The sum of 2 and 4 is 6. Therefore index<sub>1</sub> = 1, index<sub>2</sub> = 3. We return [1, 3].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> numbers = [<u>-1</u>,<u>0</u>], target = -1
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The sum of -1 and 0 is -1. Therefore index<sub>1</sub> = 1, index<sub>2</sub> = 2. We return [1, 2].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= numbers.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= numbers[i] &lt;= 1000</code></li>
	<li><code>numbers</code> is sorted in <strong>non-decreasing order</strong>.</li>
	<li><code>-1000 &lt;= target &lt;= 1000</code></li>
	<li>The tests are generated such that there is <strong>exactly one solution</strong>.</li>
</ul>


### ZH-CN:
<p>给你一个下标从 <strong>1</strong> 开始的整数数组&nbsp;<code>numbers</code> ，该数组已按<strong><em> </em>非递减顺序排列&nbsp; </strong>，请你从数组中找出满足相加之和等于目标数&nbsp;<code>target</code> 的两个数。如果设这两个数分别是 <code>numbers[index<sub>1</sub>]</code> 和 <code>numbers[index<sub>2</sub>]</code> ，则 <code>1 &lt;= index<sub>1</sub> &lt; index<sub>2</sub> &lt;= numbers.length</code> 。</p>

<p>以长度为 2 的整数数组 <code>[index<sub>1</sub>, index<sub>2</sub>]</code> 的形式返回这两个整数的下标 <code>index<sub>1</sub></code><em> </em>和<em> </em><code>index<sub>2</sub></code>。</p>

<p>你可以假设每个输入 <strong>只对应唯一的答案</strong> ，而且你 <strong>不可以</strong> 重复使用相同的元素。</p>

<p>你所设计的解决方案必须只使用常量级的额外空间。</p>
&nbsp;

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>numbers = [<strong><em>2</em></strong>,<strong><em>7</em></strong>,11,15], target = 9
<strong>输出：</strong>[1,2]
<strong>解释：</strong>2 与 7 之和等于目标数 9 。因此 index<sub>1</sub> = 1, index<sub>2</sub> = 2 。返回 [1, 2] 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>numbers = [<strong><em>2</em></strong>,3,<strong><em>4</em></strong>], target = 6
<strong>输出：</strong>[1,3]
<strong>解释：</strong>2 与 4 之和等于目标数 6 。因此 index<sub>1</sub> = 1, index<sub>2</sub> = 3 。返回 [1, 3] 。</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>numbers = [<strong><em>-1</em></strong>,<strong><em>0</em></strong>], target = -1
<strong>输出：</strong>[1,2]
<strong>解释：</strong>-1 与 0 之和等于目标数 -1 。因此 index<sub>1</sub> = 1, index<sub>2</sub> = 2 。返回 [1, 2] 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= numbers.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= numbers[i] &lt;= 1000</code></li>
	<li><code>numbers</code> 按 <strong>非递减顺序</strong> 排列</li>
	<li><code>-1000 &lt;= target &lt;= 1000</code></li>
	<li><strong>仅存在一个有效答案</strong></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/two-sum-ii-input-array-is-sorted/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 12 ms | 15.2 MB | 2022/08/21 22:52 |

```cpp

class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        const int n = numbers.size();
        int l = 0, r = n - 1;

        while(l < r){
            int val = numbers[l] + numbers[r];
            if(val == target) return {l + 1, r + 1};
            if(val > target) r--;
            else l++;
        }
        return {-1, -1};
    }
};

```
## My Notes - 我的笔记


No notes

