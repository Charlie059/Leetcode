
# 977. Squares of a Sorted Array - 有序数组的平方

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer array <code>nums</code> sorted in <strong>non-decreasing</strong> order, return <em>an array of <strong>the squares of each number</strong> sorted in non-decreasing order</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [-4,-1,0,3,10]
<strong>Output:</strong> [0,1,9,16,100]
<strong>Explanation:</strong> After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-7,-3,2,3,11]
<strong>Output:</strong> [4,9,9,49,121]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code><span>1 &lt;= nums.length &lt;= </span>10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>nums</code> is sorted in <strong>non-decreasing</strong> order.</li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Squaring each element and sorting the new array is very trivial, could you find an <code>O(n)</code> solution using a different approach?

### ZH-CN:
<p>给你一个按 <strong>非递减顺序</strong> 排序的整数数组 <code>nums</code>，返回 <strong>每个数字的平方</strong> 组成的新数组，要求也按 <strong>非递减顺序</strong> 排序。</p>

<ul>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [-4,-1,0,3,10]
<strong>输出：</strong>[0,1,9,16,100]
<strong>解释：</strong>平方后，数组变为 [16,1,0,9,100]
排序后，数组变为 [0,1,9,16,100]</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [-7,-3,2,3,11]
<strong>输出：</strong>[4,9,9,49,121]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code><span>1 <= nums.length <= </span>10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup></code></li>
	<li><code>nums</code> 已按 <strong>非递减顺序</strong> 排序</li>
</ul>

<p> </p>

<p><strong>进阶：</strong></p>

<ul>
	<li>请你<span style="color: rgb(36, 41, 46); font-family: -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Helvetica, Arial, sans-serif, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;; font-size: 14px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: rgb(255, 255, 255); text-decoration-style: initial; text-decoration-color: initial; display: inline !important; float: none;">设计时间复杂度为 <code>O(n)</code> 的算法解决本问题</span></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/squares-of-a-sorted-array/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| javascript  | 100 ms | 47.5 MB | 2023/02/11 11:00 |

```javascript

/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortedSquares = function(nums) {
    const n = nums.length;
    const ans = new Array(n).fill(0);

    let l = 0, r = n - 1;
    let i = n - 1;
    while(l <= r){
        if(nums[l] * nums[l] > nums[r] * nums[r]){
            ans[i--] = nums[l] * nums[l++];
        }else{
            ans[i--] = nums[r] * nums[r--];
        }
    }
    return ans;
};

```
## My Notes - 我的笔记


No notes

