
# 面试题 17.19. Missing Two LCCI - 消失的两个数字

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Bit Manipulation-位运算-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an array with all the numbers from 1 to N appearing exactly once, except for two number that is missing. How can you find the missing number in O(N) time and 0(1) space?</p>

<p>You can return the missing numbers in any order.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <code>[1]</code>
<strong>Output: </strong>[2,3]</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <code>[2,3]</code>
<strong>Output: </strong>[1,4]</pre>

<p><strong>Note: </strong></p>

<ul>
	<li><code>nums.length &lt;=&nbsp;30000</code></li>
</ul>


### ZH-CN:
<p>给定一个数组，包含从 1 到 N 所有的整数，但其中缺了两个数字。你能在 O(N) 时间内只用 O(1) 的空间找到它们吗？</p>

<p>以任意顺序返回这两个数字均可。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[1]</code>
<strong>输出: </strong>[2,3]</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <code>[2,3]</code>
<strong>输出: </strong>[1,4]</pre>

<p><strong>提示：</strong></p>

<ul>
	<li><code>nums.length &lt;=&nbsp;30000</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/missing-two-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/missing-two-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 24 ms | 21.8 MB | 2022/10/03 9:09 |

```cpp

class Solution {
public:
    vector<int> missingTwo(vector<int>& nums) {
        const int n = nums.size() + 2;
        int realSum = accumulate(nums.begin(), nums.end(), 0);
        int predictSum = n * (n + 1) / 2;
        int diff = predictSum - realSum;
        int halfDiff = diff / 2;
        int halfDiffSum = halfDiff * (halfDiff + 1) / 2;

        for(int i = 0; i < nums.size(); i++){
            if(nums[i] <= halfDiff){
                halfDiffSum = halfDiffSum - nums[i];
            }
        }

        return {halfDiffSum, diff - halfDiffSum};
    }
};

```
## My Notes - 我的笔记


No notes

