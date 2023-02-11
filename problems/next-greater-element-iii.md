
# 556. Next Greater Element III - 下一个更大元素 III

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a positive integer <code>n</code>, find <em>the smallest integer which has exactly the same digits existing in the integer</em> <code>n</code> <em>and is greater in value than</em> <code>n</code>. If no such positive integer exists, return <code>-1</code>.</p>

<p><strong>Note</strong> that the returned integer should fit in <strong>32-bit integer</strong>, if there is a valid answer but it does not fit in <strong>32-bit integer</strong>, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> n = 12
<strong>Output:</strong> 21
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> n = 21
<strong>Output:</strong> -1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>


### ZH-CN:
<p>给你一个正整数 <code>n</code> ，请你找出符合条件的最小整数，其由重新排列 <code>n</code><strong> </strong>中存在的每位数字组成，并且其值大于 <code>n</code> 。如果不存在这样的正整数，则返回 <code>-1</code> 。</p>

<p><strong>注意</strong> ，返回的整数应当是一个 <strong>32 位整数</strong> ，如果存在满足题意的答案，但不是 <strong>32 位整数</strong> ，同样返回 <code>-1</code> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 12
<strong>输出：</strong>21
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 21
<strong>输出：</strong>-1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n <= 2<sup>31</sup> - 1</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/next-greater-element-iii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/next-greater-element-iii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6.2 MB | 2022/07/05 9:40 |

```cpp

class Solution {
public:
    int nextGreaterElement(int n) {
        vector<int> digits;

        // Get digits from n
        while(true){
            if(n <= 0) break;
            digits.emplace_back(n % 10);
            n /= 10;
        }
        
        int m = digits.size();
        reverse(digits.begin(), digits.end());

        int i = m - 1, j = m - 1;

        while(i >= 1){
            if(digits[i] > digits[i - 1]){
                break;
            }
            i--;
        }
        i--;

        if(i == -1) return -1;

        while(j >= 0){
            if(digits[i] < digits[j]){
                break;
            }
            j--;
        }


        swap(digits[i], digits[j]);
        reverse(digits.begin() + i + 1, digits.end());

        for(int k = 0; k < m; k++){
            cout << digits[k] << " ,";
        }
            
        long ans = 0;
        for(int k = 0; k < m; k++){
            ans += digits[m - k - 1] * pow(10, k);
        }
            cout << ans;
        return ans > INT_MAX ? -1 : ans;
    }
};

```
## My Notes - 我的笔记


No notes

