
# 907. Sum of Subarray Minimums - 子数组的最小值之和

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Stack-栈-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Monotonic Stack-单调栈-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an array of integers arr, find the sum of <code>min(b)</code>, where <code>b</code> ranges over every (contiguous) subarray of <code>arr</code>. Since the answer may be large, return the answer <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [3,1,2,4]
<strong>Output:</strong> 17
<strong>Explanation:</strong> 
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. 
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.
Sum is 17.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [11,81,94,43,3]
<strong>Output:</strong> 444
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= arr[i] &lt;= 3 * 10<sup>4</sup></code></li>
</ul>


### ZH-CN:
<p>给定一个整数数组 <code>arr</code>，找到 <code>min(b)</code> 的总和，其中 <code>b</code> 的范围为 <code>arr</code> 的每个（连续）子数组。</p>

<p>由于答案可能很大，因此<strong> 返回答案模 <code>10^9 + 7</code></strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>arr = [3,1,2,4]
<strong>输出：</strong>17
<strong>解释：
</strong>子数组为<strong> </strong>[3]，[1]，[2]，[4]，[3,1]，[1,2]，[2,4]，[3,1,2]，[1,2,4]，[3,1,2,4]。 
最小值为 3，1，2，4，1，1，2，1，1，1，和为 17。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>arr = [11,81,94,43,3]
<strong>输出：</strong>444
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= arr.length <= 3 * 10<sup>4</sup></code></li>
	<li><code>1 <= arr[i] <= 3 * 10<sup>4</sup></code></li>
</ul>

<p> </p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/sum-of-subarray-minimums/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/sum-of-subarray-minimums/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 96 ms | 45.9 MB | 2022/10/27 23:35 |

```cpp

class Solution {
public:
    int sumSubarrayMins(vector<int>& arr) {
        const int n = arr.size();
        const int mod = pow(10, 9) + 7;

        stack<long> stk1, stk2;
        vector<long> left(n);
        vector<long> right(n);


        for(int i = 0; i < n; i++){
            while(!stk1.empty() && arr[stk1.top()] > arr[i]) stk1.pop();
            if(stk1.empty()) left[i] = -1;
            else left[i] = stk1.top();
            stk1.push(i);
        }

        for(int i = n - 1; i >= 0; i--){
            while(!stk2.empty() && arr[stk2.top()] >= arr[i]) stk2.pop();
            if(stk2.empty()) right[i] = n;
            else right[i] = stk2.top();
            stk2.push(i);
        }

        long ans = 0;
        for(int i = 0; i < n; i++){
            ans = (ans + (i - left[i]) * (right[i] - i) * arr[i]) % mod;
        }

        return ans;

    }
};

```
## My Notes - 我的笔记


No notes

