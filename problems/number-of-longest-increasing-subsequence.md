
# 673. Number of Longest Increasing Subsequence - 最长递增子序列的个数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Binary Indexed Tree-树状数组-blue.svg">   <img src="https://img.shields.io/badge/Segment Tree-线段树-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer array&nbsp;<code>nums</code>, return <em>the number of longest increasing subsequences.</em></p>

<p><strong>Notice</strong> that the sequence has to be <strong>strictly</strong> increasing.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,5,4,7]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The two longest increasing subsequences are [1, 3, 4, 7] and [1, 3, 5, 7].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,2,2,2,2]
<strong>Output:</strong> 5
<strong>Explanation:</strong> The length of the longest increasing subsequence is 1, and there are 5 increasing subsequences of length 1, so output 5.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2000</code></li>
	<li><code>-10<sup>6</sup> &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
</ul>


### ZH-CN:
<p>给定一个未排序的整数数组<meta charset="UTF-8" />&nbsp;<code>nums</code>&nbsp;，&nbsp;<em>返回最长递增子序列的个数</em>&nbsp;。</p>

<p><strong>注意</strong>&nbsp;这个数列必须是 <strong>严格</strong> 递增的。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,3,5,4,7]
<strong>输出:</strong> 2
<strong>解释:</strong> 有两个最长递增子序列，分别是 [1, 3, 4, 7] 和[1, 3, 5, 7]。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [2,2,2,2,2]
<strong>输出:</strong> 5
<strong>解释:</strong> 最长递增子序列的长度是1，并且存在5个子序列的长度为1，因此输出5。
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong>&nbsp;</p>

<p><meta charset="UTF-8" /></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2000</code></li>
	<li><code>-10<sup>6</sup>&nbsp;&lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/number-of-longest-increasing-subsequence/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/number-of-longest-increasing-subsequence/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 164 ms | 12.9 MB | 2022/11/09 23:49 |

```cpp

class Solution {
public:
    int findNumberOfLIS(vector<int>& nums) {
        const int n = nums.size();
        vector<int> dp(n, 1);
        vector<int> cnt(n, 1);

        for(int i = 1; i < n; i++){
            int cnt_ = 1;
            int maxVal = 0;
            for(int j = i - 1; j >= 0; j--){
                if(nums[j] < nums[i]){
                    if(dp[j] > maxVal){
                        maxVal = dp[j];
                        cnt_ = cnt[j];
                    }else if(dp[j] == maxVal){
                        cnt_ += cnt[j];
                    }
                }
            }
            dp[i] = maxVal + 1;
            cnt[i] = cnt_;
        }

        int ans = 0;

        int maxVal = *max_element(dp.begin(), dp.end());
        for(int i = 0; i < n; i++){
            if(dp[i] == maxVal) ans += cnt[i];
        }

        for(int i = 0; i < n; i++) cout << dp[i] << " ";
        cout << endl;
        for(int i = 0; i < n; i++) cout << cnt[i] << " ";
        
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

