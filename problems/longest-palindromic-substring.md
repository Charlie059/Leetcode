
# 5. Longest Palindromic Substring - 最长回文子串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code>, return <em>the longest</em> <span data-keyword="palindromic-string"><em>palindromic</em></span> <span data-keyword="substring-nonempty"><em>substring</em></span> in <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;babad&quot;
<strong>Output:</strong> &quot;bab&quot;
<strong>Explanation:</strong> &quot;aba&quot; is also a valid answer.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;cbbd&quot;
<strong>Output:</strong> &quot;bb&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consist of only digits and English letters.</li>
</ul>


### ZH-CN:
<p>给你一个字符串 <code>s</code>，找到 <code>s</code> 中最长的回文子串。</p>

<p>如果字符串的反序与原始字符串相同，则该字符串称为回文字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "babad"
<strong>输出：</strong>"bab"
<strong>解释：</strong>"aba" 同样是符合题意的答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "cbbd"
<strong>输出：</strong>"bb"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> 仅由数字和英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/longest-palindromic-substring/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/longest-palindromic-substring/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 388 ms | 22.2 MB | 2023/01/23 11:07 |

```cpp

class Solution {
public:
    string longestPalindrome(string s) {
        const int n = s.length();
        vector<vector<bool>> isPalindrome(n, vector<bool>(n, false));
    
        pair<int, int> ans = {0, 0};
        int maxLen = 0;
        int cnt = 0;
        for(int k = 0; k < n; k++){
                for(int l = 0; l < n; l++){
                    int i = 0 + l, j = i + cnt;
                    if(i >= n || j >= n) continue;
                    if(i == j) isPalindrome[i][j] = 1;
                    else{
                        if(s[i] != s[j]) isPalindrome[i][j] = 0;
                        else{
                            if(i + 1 == j) isPalindrome[i][j] = 1;
                            else{
                                isPalindrome[i][j] = isPalindrome[i + 1][j - 1];
                            }
                        }
                        if(isPalindrome[i][j]){
                            if(maxLen < j - i + 1){
                                maxLen = j - i + 1;
                                ans = {i, j};
                            }
                        }
                    }
                }
                cnt++;
        }

        // for(int i = 0; i < n; i++){
        //     for(int j = 0; j < n; j++){
        //         cout << isPalindrome[i][j] << " ";
        //     }
        //     cout << endl;
        // }
        
        return s.substr(ans.first, ans.second - ans.first + 1);
    }
};

```
## My Notes - 我的笔记


No notes

