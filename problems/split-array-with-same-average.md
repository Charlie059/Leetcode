
# 805. Split Array With Same Average - 数组的均值分割

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Bit Manipulation-位运算-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Bitmask-状态压缩-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an integer array <code>nums</code>.</p>

<p>You should move each element of <code>nums</code> into one of the two arrays <code>A</code> and <code>B</code> such that <code>A</code> and <code>B</code> are non-empty, and <code>average(A) == average(B)</code>.</p>

<p>Return <code>true</code> if it is possible to achieve that and <code>false</code> otherwise.</p>

<p><strong>Note</strong> that for an array <code>arr</code>, <code>average(arr)</code> is the sum of all the elements of <code>arr</code> over the length of <code>arr</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5,6,7,8]
<strong>Output:</strong> true
<strong>Explanation:</strong> We can split the array into [1,4,5,8] and [2,3,6,7], and both of them have an average of 4.5.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,1]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 30</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>


### ZH-CN:
<p>给定你一个整数数组<meta charset="UTF-8" />&nbsp;<code>nums</code></p>

<p>我们要将<meta charset="UTF-8" />&nbsp;<code>nums</code>&nbsp;数组中的每个元素移动到&nbsp;<code>A</code>&nbsp;数组 或者&nbsp;<code>B</code>&nbsp;数组中，使得&nbsp;<code>A</code>&nbsp;数组和<meta charset="UTF-8" />&nbsp;<code>B</code>&nbsp;数组不为空，并且<meta charset="UTF-8" />&nbsp;<code>average(A) == average(B)</code>&nbsp;。</p>

<p>如果可以完成则返回<code>true</code>&nbsp;， 否则返回 <code>false</code>&nbsp;&nbsp;。</p>

<p><strong>注意：</strong>对于数组<meta charset="UTF-8" />&nbsp;<code>arr</code>&nbsp;, <meta charset="UTF-8" />&nbsp;<code>average(arr)</code>&nbsp;是<meta charset="UTF-8" />&nbsp;<code>arr</code>&nbsp;的所有元素的和除以<meta charset="UTF-8" />&nbsp;<code>arr</code>&nbsp;长度。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,2,3,4,5,6,7,8]
<strong>输出:</strong> true
<strong>解释: </strong>我们可以将数组分割为 [1,4,5,8] 和 [2,3,6,7], 他们的平均值都是4.5。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> nums = [3,1]
<strong>输出:</strong> false
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 30</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/split-array-with-same-average/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/split-array-with-same-average/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 1480 ms | 8.2 MB | 2022/11/13 16:49 |

```cpp

class Solution {
public:
    bool splitArraySameAverage(vector<int>& A) {
        int size=A.size();
        int sum=accumulate(A.begin(),A.end(),0);

        sort(A.begin(),A.end());
        //遍历子数组的长度，仅需要遍历两个子数组中短的那个即可，短的满足了，长的也满足
        for(int i=1;i<=size/2;i++){
            //要满足子数组平均数等于整个数组平均数，则有sum*i==size*subSum,i为子数组长度，
            //subNum为子数组和，显然subNum是整数
            if(sum*i%size==0&&dfs(0,size,i,sum*i/size,A)==true){
                return true;
            }
        }

        return false;
    }

    bool dfs(int start,int size,int cnt,int target,vector<int>&A){
        if(cnt==0){
            return target==0;
        }

        for(int i=start;i<size-cnt+1;i++){
            //如果出现了重复的值，之前就已经考虑这种情况了，剪枝
            if(i!=start&&A[i]==A[i-1]){
                continue;
            }
            //递归求解
            if(dfs(i+1,size,cnt-1,target-A[i],A)==true){
                return true;
            }
        }

        return false;
    }
};

```
## My Notes - 我的笔记


No notes

