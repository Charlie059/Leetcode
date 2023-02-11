
# 131. Palindrome Partitioning - 分割回文串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Backtracking-回溯-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code>, partition <code>s</code> such that every <span data-keyword="substring-nonempty">substring</span> of the partition is a <span data-keyword="palindrome-string"><strong>palindrome</strong></span>. Return <em>all possible palindrome partitioning of </em><code>s</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> s = "aab"
<strong>Output:</strong> [["a","a","b"],["aa","b"]]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> s = "a"
<strong>Output:</strong> [["a"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 16</code></li>
	<li><code>s</code> contains only lowercase English letters.</li>
</ul>


### ZH-CN:
<p>给你一个字符串 <code>s</code>，请你将<em> </em><code>s</code><em> </em>分割成一些子串，使每个子串都是 <strong>回文串</strong> 。返回 <code>s</code> 所有可能的分割方案。</p>

<p><strong>回文串</strong> 是正着读和反着读都一样的字符串。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "aab"
<strong>输出：</strong>[["a","a","b"],["aa","b"]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "a"
<strong>输出：</strong>[["a"]]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 16</code></li>
	<li><code>s</code> 仅由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/palindrome-partitioning/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/palindrome-partitioning/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 100 ms | 73.9 MB | 2022/12/09 17:28 |

```cpp

class Solution {
public:
    vector<vector<bool>> isPalindrome;

    vector<vector<string>> ans;
    vector<string> path;

    void dfs(string& s, int startIdx){
        if(startIdx == s.length()){
            ans.emplace_back(path);
            return;
        }

        for(int i = startIdx; i < s.length(); i++){
            int l = startIdx, r = i;
            if(isPalindrome[l][r]){
                string t = s.substr(startIdx, i - startIdx + 1);
                path.emplace_back(t);
                dfs(s, i + 1);
                path.pop_back();
            }
        }
    }
    
    vector<vector<string>> partition(string s) {
        // Build isPalindrome
        const int n = s.length();
        isPalindrome.resize(n, vector<bool>(n, true));

        for(int l = 2; l <= n; l++){
            for(int i = 0, j = i + l - 1; j < n; i++, j++){
                isPalindrome[i][j] = isPalindrome[i + 1][j - 1] && s[i] == s[j];
            }
        }

        dfs(s, 0);

        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

