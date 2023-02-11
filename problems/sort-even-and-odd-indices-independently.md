
# 2164. Sort Even and Odd Indices Independently - 对奇偶下标分别排序

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code>. Rearrange the values of <code>nums</code> according to the following rules:</p>

<ol>
	<li>Sort the values at <strong>odd indices</strong> of <code>nums</code> in <strong>non-increasing</strong> order.

	<ul>
		<li>For example, if <code>nums = [4,<strong><u>1</u></strong>,2,<u><strong>3</strong></u>]</code> before this step, it becomes <code>[4,<u><strong>3</strong></u>,2,<strong><u>1</u></strong>]</code> after. The values at odd indices <code>1</code> and <code>3</code> are sorted in non-increasing order.</li>
	</ul>
	</li>
	<li>Sort the values at <strong>even indices</strong> of <code>nums</code> in <strong>non-decreasing</strong> order.
	<ul>
		<li>For example, if <code>nums = [<u><strong>4</strong></u>,1,<u><strong>2</strong></u>,3]</code> before this step, it becomes <code>[<u><strong>2</strong></u>,1,<u><strong>4</strong></u>,3]</code> after. The values at even indices <code>0</code> and <code>2</code> are sorted in non-decreasing order.</li>
	</ul>
	</li>
</ol>

<p>Return <em>the array formed after rearranging the values of</em> <code>nums</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,1,2,3]
<strong>Output:</strong> [2,3,4,1]
<strong>Explanation:</strong> 
First, we sort the values present at odd indices (1 and 3) in non-increasing order.
So, nums changes from [4,<strong><u>1</u></strong>,2,<strong><u>3</u></strong>] to [4,<u><strong>3</strong></u>,2,<strong><u>1</u></strong>].
Next, we sort the values present at even indices (0 and 2) in non-decreasing order.
So, nums changes from [<u><strong>4</strong></u>,1,<strong><u>2</u></strong>,3] to [<u><strong>2</strong></u>,3,<u><strong>4</strong></u>,1].
Thus, the array formed after rearranging the values is [2,3,4,1].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1]
<strong>Output:</strong> [2,1]
<strong>Explanation:</strong> 
Since there is exactly one odd index and one even index, no rearrangement of values takes place.
The resultant array formed is [2,1], which is the same as the initial array. 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 100</code></li>
</ul>


### ZH-CN:
<p>给你一个下标从 <strong>0</strong> 开始的整数数组 <code>nums</code> 。根据下述规则重排 <code>nums</code> 中的值：</p>

<ol>
	<li>按 <strong>非递增</strong> 顺序排列 <code>nums</code> <strong>奇数下标</strong> 上的所有值。

	<ul>
		<li>举个例子，如果排序前 <code>nums = [4,<em><strong>1</strong></em>,2,<em><strong>3</strong></em>]</code> ，对奇数下标的值排序后变为 <code>[4,<em><strong>3</strong></em>,2,<em><strong>1</strong></em>]</code> 。奇数下标 <code>1</code> 和 <code>3</code> 的值按照非递增顺序重排。</li>
	</ul>
	</li>
	<li>按 <strong>非递减</strong> 顺序排列 <code>nums</code> <strong>偶数下标</strong> 上的所有值。
	<ul>
		<li>举个例子，如果排序前 <code>nums = [<em><strong>4</strong></em>,1,<em><strong>2</strong></em>,3]</code> ，对偶数下标的值排序后变为 <code>[<em><strong>2</strong></em>,1,<em><strong>4</strong></em>,3]</code> 。偶数下标 <code>0</code> 和 <code>2</code> 的值按照非递减顺序重排。</li>
	</ul>
	</li>
</ol>

<p>返回重排 <code>nums</code> 的值之后形成的数组。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [4,1,2,3]
<strong>输出：</strong>[2,3,4,1]
<strong>解释：</strong>
首先，按非递增顺序重排奇数下标（1 和 3）的值。
所以，nums 从 [4,<em><strong>1</strong></em>,2,<em><strong>3</strong></em>] 变为 [4,<em><strong>3</strong></em>,2,<em><strong>1</strong></em>] 。
然后，按非递减顺序重排偶数下标（0 和 2）的值。
所以，nums 从 [<em><strong>4</strong></em>,1,<em><strong>2</strong></em>,3] 变为 [<em><strong>2</strong></em>,3,<em><strong>4</strong></em>,1] 。
因此，重排之后形成的数组是 [2,3,4,1] 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [2,1]
<strong>输出：</strong>[2,1]
<strong>解释：</strong>
由于只有一个奇数下标和一个偶数下标，所以不会发生重排。
形成的结果数组是 [2,1] ，和初始数组一样。 
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 100</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/sort-even-and-odd-indices-independently/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/sort-even-and-odd-indices-independently/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 12 MB | 2022/02/06 20:01 |

```cpp

class Solution {
public:
    vector<int> sortEvenOdd(vector<int>& nums) {
        vector<int> odd;
        vector<int> even;
        vector<int> ans;
        
        for(int i = 0; i < nums.size(); i++){
            if(i % 2 == 0) odd.push_back(nums[i]);
            else even.push_back(nums[i]);
        }
        sort(odd.begin(), odd.end());
        sort(even.begin(), even.end(), std::greater<int>());
        
        for(int i = 0; i < nums.size() / 2; i++){
            ans.push_back(odd[i]);
            ans.push_back(even[i]);
        }
        
        if(nums.size() % 2 == 1){
            ans.push_back(odd[odd.size()- 1]);
        }
        
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

