
# 2180. Count Integers With Even Digit Sum - 统计各位数字之和为偶数的整数个数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Simulation-模拟-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a positive integer <code>num</code>, return <em>the number of positive integers <strong>less than or equal to</strong></em> <code>num</code> <em>whose digit sums are <strong>even</strong></em>.</p>

<p>The <strong>digit sum</strong> of a positive integer is the sum of all its digits.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 4
<strong>Output:</strong> 2
<strong>Explanation:</strong>
The only integers less than or equal to 4 whose digit sums are even are 2 and 4.    
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 30
<strong>Output:</strong> 14
<strong>Explanation:</strong>
The 14 integers less than or equal to 30 whose digit sums are even are
2, 4, 6, 8, 11, 13, 15, 17, 19, 20, 22, 24, 26, and 28.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 1000</code></li>
</ul>


### ZH-CN:
<p>给你一个正整数 <code>num</code> ，请你统计并返回 <strong>小于或等于</strong> <code>num</code> 且各位数字之和为 <strong>偶数</strong> 的正整数的数目。</p>

<p>正整数的 <strong>各位数字之和</strong> 是其所有位上的对应数字相加的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>num = 4
<strong>输出：</strong>2
<strong>解释：</strong>
只有 2 和 4 满足小于等于 4 且各位数字之和为偶数。    
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>num = 30
<strong>输出：</strong>14
<strong>解释：</strong>
只有 14 个整数满足小于等于 30 且各位数字之和为偶数，分别是： 
2、4、6、8、11、13、15、17、19、20、22、24、26 和 28 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 1000</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/count-integers-with-even-digit-sum/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/count-integers-with-even-digit-sum/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 5.9 MB | 2023/01/05 16:26 |

```cpp

class Solution {
public:
    inline int helper(int num){
        if(num < 2) return 0;
        else if(num < 4) return 1;
        else if(num < 6) return 2;
        else if(num < 8) return 3;
        else return 4;
    }
    inline int helperEven(int num){
        if(num < 2) return 1;
        else if(num < 4) return 2;
        else if(num < 6) return 3;
        else if(num < 8) return 4;
        else return 5;
    }
    inline int helperOdd(int num){
        if(num < 1) return 0;
        else if(num < 3) return 1;
        else if(num < 5) return 2;
        else if(num < 7) return 3;
        else if(num < 9) return 4;
        else return 5;
    }
    int countEven(int num) {
        if(num < 10) return helper(num);
        int a, b, c;

        a = (num / 10);
        c = a - 1;

        int s = 0;
        while(a){
            s += a % 10;
            a /= 10;
        }
        if(s % 2 == 0) b = helperEven(num % 10);
        else b = helperOdd(num % 10);

   
        return c * 5 + b + 4;
    }
};

```
## My Notes - 我的笔记


No notes

