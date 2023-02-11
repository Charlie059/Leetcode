
# 剑指 Offer 03. 数组中重复的数字 LCOF - 数组中重复的数字

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">  


## Description - 题目描述

### EN:
<p>English description is not available for the problem. Please switch to Chinese.</p>


### ZH-CN:
<p>找出数组中重复的数字。</p>

<p><br>
在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>
[2, 3, 1, 0, 2, 5, 3]
<strong>输出：</strong>2 或 3 
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>2 &lt;= n &lt;= 100000</code></p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 28 ms | 22.4 MB | 2022/10/31 14:59 |

```cpp

class Solution {
public:
    //[2, 3, 1, 0, 2, 5, 3]
    //[1, 3, 2, 0, 2, 5, 3]
    //[1, 0, 2, 3, 2, 5, 3]
    //[0, 1, 2, 3, 2, 5, 3]
    //[0, 1, 2, 3, 2] => return 2
    int findRepeatNumber(vector<int>& nums) {
        const int n = nums.size();
        for(int i = 0; i < n; i++){
            while(0 <= nums[i] && nums[i] <= n - 1 && nums[i] != i){
                if(nums[i] == nums[nums[i]]) return nums[i];
                swap(nums[i], nums[nums[i]]);
            }
        }
        return -1;
    }
};

```
## My Notes - 我的笔记


No notes

