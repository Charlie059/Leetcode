
# 224. Basic Calculator - 基本计算器

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Stack-栈-blue.svg">   <img src="https://img.shields.io/badge/Recursion-递归-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code> representing a valid expression, implement a basic calculator to evaluate it, and return <em>the result of the evaluation</em>.</p>

<p><strong>Note:</strong> You are <strong>not</strong> allowed to use any built-in function which evaluates strings as mathematical expressions, such as <code>eval()</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1 + 1&quot;
<strong>Output:</strong> 2
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot; 2-1 + 2 &quot;
<strong>Output:</strong> 3
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(1+(4+5+2)-3)+(6+8)&quot;
<strong>Output:</strong> 23
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 3 * 10<sup>5</sup></code></li>
	<li><code>s</code> consists of digits, <code>&#39;+&#39;</code>, <code>&#39;-&#39;</code>, <code>&#39;(&#39;</code>, <code>&#39;)&#39;</code>, and <code>&#39; &#39;</code>.</li>
	<li><code>s</code> represents a valid expression.</li>
	<li><code>&#39;+&#39;</code> is <strong>not</strong> used as a unary operation (i.e., <code>&quot;+1&quot;</code> and <code>&quot;+(2 + 3)&quot;</code> is invalid).</li>
	<li><code>&#39;-&#39;</code> could be used as a unary operation (i.e., <code>&quot;-1&quot;</code> and <code>&quot;-(2 + 3)&quot;</code> is valid).</li>
	<li>There will be no two consecutive operators in the input.</li>
	<li>Every number and running calculation will fit in a signed 32-bit integer.</li>
</ul>


### ZH-CN:
<p>给你一个字符串表达式 <code>s</code> ，请你实现一个基本计算器来计算并返回它的值。</p>

<p>注意:不允许使用任何将字符串作为数学表达式计算的内置函数，比如 <code>eval()</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "1 + 1"
<strong>输出：</strong>2
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = " 2-1 + 2 "
<strong>输出：</strong>3
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "(1+(4+5+2)-3)+(6+8)"
<strong>输出：</strong>23
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 3&nbsp;* 10<sup>5</sup></code></li>
	<li><code>s</code> 由数字、<code>'+'</code>、<code>'-'</code>、<code>'('</code>、<code>')'</code>、和 <code>' '</code> 组成</li>
	<li><code>s</code> 表示一个有效的表达式</li>
	<li><font color="#c7254e"><font face="Menlo, Monaco, Consolas, Courier New, monospace"><span style="font-size:12.6px"><span style="background-color:#f9f2f4">'+'</span></span></font></font> 不能用作一元运算(例如， <font color="#c7254e"><font face="Menlo, Monaco, Consolas, Courier New, monospace"><span style="font-size:12.6px"><span style="background-color:#f9f2f4">"+1"</span></span></font></font>&nbsp;和 <code>"+(2 + 3)"</code>&nbsp;无效)</li>
	<li><font color="#c7254e"><font face="Menlo, Monaco, Consolas, Courier New, monospace"><span style="font-size:12.6px"><span style="background-color:#f9f2f4">'-'</span></span></font></font> 可以用作一元运算(即 <font color="#c7254e"><font face="Menlo, Monaco, Consolas, Courier New, monospace"><span style="font-size:12.6px"><span style="background-color:#f9f2f4">"-1"</span></span></font></font>&nbsp;和 <code>"-(2 + 3)"</code>&nbsp;是有效的)</li>
	<li>输入中不存在两个连续的操作符</li>
	<li>每个数字和运行的计算将适合于一个有符号的 32位 整数</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/basic-calculator/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/basic-calculator/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 20 ms | 9 MB | 2022/08/11 17:07 |

```cpp

class Solution {
public:
    void calc(stack<int> & nums, stack<char> & ops){
        if(nums.size() < 2 || ops.empty()) return;

        int b = nums.top();
        nums.pop();
        int a = nums.top();
        nums.pop();
        char op = ops.top();
        ops.pop();
        nums.emplace(op == '+' ? a + b : a - b);
    }
    void replace(string & s){
        int pos = s.find(" ");
        while(pos != - 1){
            s.replace(pos, 1, "");
            pos = s.find(" ");
        }
    }
    int calculate(string s) {
        stack<int> nums;
        stack<char> ops;
        nums.push(0);
        replace(s); // remove all spaces

        const int n = s.length();

        for(int i = 0; i < n; i++){
            char c = s[i];
            if(c == '(') ops.emplace(c);
            else if(c == ')'){
                //Calculate unitl reach the prev '('
                while(!ops.empty()){
                    char op = ops.top();
                    if(op != '(') calc(nums, ops);
                    else{
                        ops.pop();
                        break;
                    }
                    
                }
            }else{
                if(isdigit(c)){
                    int num = 0;
                    while(i < n && isdigit(s[i]))  num = num * 10 + (s[i++] - '0');
                    nums.emplace(num);
                    i--;
                }else{
                    if(i > 0 && (s[i - 1] == '(' || s[i - 1] == '+' || s[i - 1] == '-')) nums.emplace(0);

                    while(!ops.empty() && ops.top() != '(') calc(nums, ops);

                    ops.emplace(c);
                }
            }
        }

        while(!ops.empty()) calc(nums, ops);
        return nums.top();
    }
};

```
## My Notes - 我的笔记


No notes

