
# 504. Base 7 - 七进制数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer <code>num</code>, return <em>a string of its <strong>base 7</strong> representation</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> num = 100
<strong>Output:</strong> "202"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> num = -7
<strong>Output:</strong> "-10"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-10<sup>7</sup> &lt;= num &lt;= 10<sup>7</sup></code></li>
</ul>


### ZH-CN:
<p>给定一个整数 <code>num</code>，将其转化为 <strong>7 进制</strong>，并以字符串形式输出。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> num = 100
<strong>输出:</strong> "202"
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> num = -7
<strong>输出:</strong> "-10"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>-10<sup>7</sup>&nbsp;&lt;= num &lt;= 10<sup>7</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/base-7/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/base-7/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 5.8 MB | 2022/07/29 18:58 |

```cpp

class Solution {
public:
    string convertToBase7(int num) {
        if(num == 0) return "0";
        bool negative = num < 0 ? true : false;
        string ans;
        num = abs(num);

        while(num != 0){
            int a = num % 7;
            ans += a + '0';
            num /= 7;
        }

        if(negative) ans.push_back('-');
        reverse(ans.begin(), ans.end());
        return ans;

    }
};

```
## My Notes - 我的笔记


No notes

