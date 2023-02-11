
# 22. Generate Parentheses - 括号生成

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Backtracking-回溯-blue.svg">  


## Description - 题目描述

### EN:
<p>Given <code>n</code> pairs of parentheses, write a function to <em>generate all combinations of well-formed parentheses</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> ["((()))","(()())","(())()","()(())","()()()"]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> ["()"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>


### ZH-CN:
<p>数字 <code>n</code>&nbsp;代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 <strong>有效的 </strong>括号组合。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>["((()))","(()())","(())()","()(())","()()()"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>["()"]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/generate-parentheses/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/generate-parentheses/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 116 ms | 156.6 MB | 2023/01/24 11:05 |

```cpp

class Solution {
public:
    string path;
    vector<string> ans;

    bool isVaild(const string& s){
        stack<char> stk;
        const int n = s.length();
        for(int i = 0; i < n; i++){
            if(s[i] == '(') stk.push(')');
            else{
                if(stk.empty()) return false;
                else{
                    stk.pop();
                }
            }
        }
        return stk.empty();
    }
    void dfs(const int n, const string& s){
        if(path.size() == 2 * n){
            if(isVaild(path)) ans.emplace_back(path);
            return;
        }

        for(int i = 0; i < 2; i++){
            path += s[i];
            dfs(n, s);
            path.pop_back();
        }
    }
    vector<string> generateParenthesis(int n) {
        string str = "()";
        dfs(n, str);
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

