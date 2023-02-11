
# 43. Multiply Strings - 字符串相乘

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Simulation-模拟-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two non-negative integers <code>num1</code> and <code>num2</code> represented as strings, return the product of <code>num1</code> and <code>num2</code>, also represented as a string.</p>

<p><strong>Note:</strong>&nbsp;You must not use any built-in BigInteger library or convert the inputs to integer directly.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> num1 = "2", num2 = "3"
<strong>Output:</strong> "6"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> num1 = "123", num2 = "456"
<strong>Output:</strong> "56088"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 200</code></li>
	<li><code>num1</code> and <code>num2</code> consist of digits only.</li>
	<li>Both <code>num1</code> and <code>num2</code>&nbsp;do not contain any leading zero, except the number <code>0</code> itself.</li>
</ul>


### ZH-CN:
<p>给定两个以字符串形式表示的非负整数&nbsp;<code>num1</code>&nbsp;和&nbsp;<code>num2</code>，返回&nbsp;<code>num1</code>&nbsp;和&nbsp;<code>num2</code>&nbsp;的乘积，它们的乘积也表示为字符串形式。</p>

<p><strong>注意：</strong>不能使用任何内置的 BigInteger 库或直接将输入转换为整数。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> num1 = "2", num2 = "3"
<strong>输出:</strong> "6"</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong> num1 = "123", num2 = "456"
<strong>输出:</strong> "56088"</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 200</code></li>
	<li><code>num1</code>&nbsp;和 <code>num2</code>&nbsp;只能由数字组成。</li>
	<li><code>num1</code>&nbsp;和 <code>num2</code>&nbsp;都不包含任何前导零，除了数字0本身。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/multiply-strings/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/multiply-strings/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 16 ms | 10.4 MB | 2022/07/26 11:31 |

```cpp

class Solution {
public:
    string sum(string &str1, string &str2){
        string ans;
        const int n = str1.length();
        const int m = str2.length();
        int i = n - 1, j = m - 1;
        int carry = 0;
        while(i >= 0 || j >= 0 || carry != 0){
            int a = i >= 0 ? str1[i] - '0': 0;
            int b = j >= 0 ? str2[j] - '0': 0;
            int sum = a + b + carry;
            carry = sum / 10;
            sum = sum % 10;
            ans += sum + '0';
            i--, j--;
        }
        reverse(ans.begin(), ans.end());
        return ans;
    }
    string multiply(string num1, string num2) {
        vector<string> sum2Add;

        const int n = num1.size();
        const int m = num2.size();

        if(n < m) return multiply(num2, num1);
        if(num1 == "0" || num2 == "0") return "0";
        

        for(int j = m - 1; j >= 0; j--){
            string temp;
            for(int i = 0; i < m - j - 1; i++){
                temp += "0";
            }
            int carry = 0;
            for(int i = n - 1; i >= 0; i--){
                int a = num1[i] - '0', b = num2[j] - '0';
                int mul = carry + a * b;
                carry = mul / 10;
                mul %= 10;
                temp += mul + '0';
            }

            while(carry != 0){
                temp += (carry % 10) + '0';
                carry /= 10;
            }

            reverse(temp.begin(), temp.end());
            sum2Add.emplace_back(temp);
        }

        string ans;

        for(int i = 0; i < sum2Add.size(); i++){
            ans = sum(ans, sum2Add[i]);
        }

        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

