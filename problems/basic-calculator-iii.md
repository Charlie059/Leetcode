
# 772. Basic Calculator III - 基本计算器 III

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Stack-栈-blue.svg">   <img src="https://img.shields.io/badge/Recursion-递归-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Implement a basic calculator to evaluate a simple expression string.</p>

<p>The expression string contains only non-negative integers, <code>&#39;+&#39;</code>, <code>&#39;-&#39;</code>, <code>&#39;*&#39;</code>, <code>&#39;/&#39;</code> operators, and open <code>&#39;(&#39;</code> and closing parentheses <code>&#39;)&#39;</code>. The integer division should <strong>truncate toward zero</strong>.</p>

<p>You may assume that the given expression is always valid. All intermediate results will be in the range of <code>[-2<sup>31</sup>, 2<sup>31</sup> - 1]</code>.</p>

<p><strong>Note:</strong> You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as <code>eval()</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1+1&quot;
<strong>Output:</strong> 2
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;6-4/2&quot;
<strong>Output:</strong> 4
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;2*(5+5*2)/3+(6/2+8)&quot;
<strong>Output:</strong> 21
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of digits, <code>&#39;+&#39;</code>, <code>&#39;-&#39;</code>, <code>&#39;*&#39;</code>, <code>&#39;/&#39;</code>, <code>&#39;(&#39;</code>,&nbsp;and&nbsp;<code>&#39;)&#39;</code>.</li>
	<li><code>s</code> is a <strong>valid</strong> expression.</li>
</ul>


### ZH-CN:
<p>实现一个基本的计算器来计算简单的表达式字符串。</p>

<p>表达式字符串只包含非负整数，算符 <code>+</code>、<code>-</code>、<code>*</code>、<code>/</code> ，左括号 <code>(</code> 和右括号 <code>)</code> 。整数除法需要 <strong>向下截断</strong> 。</p>

<p>你可以假定给定的表达式总是有效的。所有的中间结果的范围均满足 <code>[-2<sup>31</sup>, 2<sup>31</sup> - 1]</code> 。</p>

<p><strong>注意：</strong>你不能使用任何将字符串作为表达式求值的内置函数，比如 <code>eval()</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "1+1"
<strong>输出：</strong>2
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "6-4/2"
<strong>输出：</strong>4
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "2*(5+5*2)/3+(6/2+8)"
<strong>输出：</strong>21
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> 由整数、<code>'+'</code>、<code>'-'</code>、<code>'*'</code>、<code>'/'</code>、<code>'('</code> 和 <code>')'</code> 组成</li>
	<li><code>s</code> 是一个 <strong>有效的</strong> 表达式</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/basic-calculator-iii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/basic-calculator-iii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.6 MB | 2022/08/11 17:54 |

```cpp

class Solution {
public:
    stack<int> nums;
    stack<char> ops;
    unordered_map<char, int> map = {
        {'+', 1},
        {'-', 1},
        {'*', 2},
        {'/', 2},
        {'%', 2},
        {'^', 3},
    };

    void clearSpaces(string & s){
        int pos = s.find(" ");
        while(pos != -1){
            s.replace(pos, 0, "");
            pos = s.find(" ");
        }
    }

    void calc(){
        if(ops.empty() || nums.size() < 2) return;
        int b = nums.top(); nums.pop();
        int a = nums.top(); nums.pop();
        int ans = 0;
        char op = ops.top(); ops.pop();

        if(op == '+') ans = a + b;
        else if(op == '-') ans = a - b;
        else if(op == '*') ans = a * b;
        else if (op == '/')  ans = a / b;
        else if (op == '^') ans = pow(a, b);
        else if (op == '%') ans = a % b;

        nums.emplace(ans);
    }

    int calculate(string s) {
        clearSpaces(s);
        const int n = s.length();

        nums.push(0);

        for(int i = 0; i < n; i++){
            char c = s[i];

            if(c == '(') ops.emplace(c);
            else if(c == ')'){
                while(!ops.empty()){
                    if(ops.top() != '(') calc();
                    else{
                        ops.pop();
                        break;
                    }
                }
            }else{
                if(isdigit(c)){
                    int num = 0;
                    while(i < n && isdigit(s[i])) num = num * 10 + (s[i++] - '0');
                    i--;
                    nums.emplace(num);
                }else{
                    if(i > 0 && (s[i - 1] == '(' || s[i - 1] == '+' || s[i - 1] == '-')){
                        nums.emplace(0);
                    }

                    while(!ops.empty() && ops.top() != '('){
                        char prev = ops.top();
                        if(map[prev] >= map[c]) calc();
                        else break;
                    }
                    ops.emplace(c);
                }
            }
        }

        while(!ops.empty()) calc();
        return nums.top();
    }
};

```
## My Notes - 我的笔记


No notes

