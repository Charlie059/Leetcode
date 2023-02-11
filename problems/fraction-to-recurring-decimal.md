
# 166. Fraction to Recurring Decimal - 分数到小数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two integers representing the <code>numerator</code> and <code>denominator</code> of a fraction, return <em>the fraction in string format</em>.</p>

<p>If the fractional part is repeating, enclose the repeating part in parentheses.</p>

<p>If multiple answers are possible, return <strong>any of them</strong>.</p>

<p>It is <strong>guaranteed</strong> that the length of the answer string is less than <code>10<sup>4</sup></code> for all the given inputs.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> numerator = 1, denominator = 2
<strong>Output:</strong> &quot;0.5&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> numerator = 2, denominator = 1
<strong>Output:</strong> &quot;2&quot;
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> numerator = 4, denominator = 333
<strong>Output:</strong> &quot;0.(012)&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;=&nbsp;numerator, denominator &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>denominator != 0</code></li>
</ul>


### ZH-CN:
<p>给定两个整数，分别表示分数的分子&nbsp;<code>numerator</code> 和分母 <code>denominator</code>，以 <strong>字符串形式返回小数</strong> 。</p>

<p>如果小数部分为循环小数，则将循环的部分括在括号内。</p>

<p>如果存在多个答案，只需返回 <strong>任意一个</strong> 。</p>

<p>对于所有给定的输入，<strong>保证</strong> 答案字符串的长度小于 <code>10<sup>4</sup></code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>numerator = 1, denominator = 2
<strong>输出：</strong>"0.5"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>numerator = 2, denominator = 1
<strong>输出：</strong>"2"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>numerator = 4, denominator = 333
<strong>输出：</strong>"0.(012)"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;=&nbsp;numerator, denominator &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>denominator != 0</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/fraction-to-recurring-decimal/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/fraction-to-recurring-decimal/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6.1 MB | 2022/08/21 10:40 |

```cpp

class Solution {
public:
    string fractionToDecimal(int numerator, int denominator) {
        long numeratorLong = numerator, denominatorLong = denominator;
        if(numeratorLong % denominatorLong == 0) return to_string(numeratorLong/denominatorLong);

        string ans;
        // Check negative
        if((numeratorLong < 0) ^ (denominatorLong < 0)) ans += "-";
        numeratorLong = abs(numeratorLong), denominatorLong = abs(denominatorLong);

        // Poress interger part
        string interger = to_string(numeratorLong / denominatorLong);
        ans = ans + interger + ".";

        // Process fraction part
        string fraction;
        unordered_map<long, int> fractionIdxMap;
        long remainder = numeratorLong % denominatorLong;
        int idx = 0;

        while(remainder != 0 && fractionIdxMap.count(remainder) == 0){
            // Add to Map
            fractionIdxMap[remainder] = idx;
            
            remainder *= 10;
            fraction += to_string(remainder / denominatorLong);
            remainder %= denominatorLong;
            idx++;
        }

        // Add Inf string
        if(remainder != 0){
            int idx = fractionIdxMap[remainder];
            fraction = fraction.substr(0, idx) + "(" + fraction.substr(idx) + ")";
        }
        ans += fraction;
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

