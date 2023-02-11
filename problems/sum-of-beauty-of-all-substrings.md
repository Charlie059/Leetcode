
# 1781. Sum of Beauty of All Substrings - 所有子字符串美丽值之和

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Counting-计数-blue.svg">  


## Description - 题目描述

### EN:
<p>The <strong>beauty</strong> of a string is the difference in frequencies between the most frequent and least frequent characters.</p>

<ul>
	<li>For example, the beauty of <code>&quot;abaacc&quot;</code> is <code>3 - 1 = 2</code>.</li>
</ul>

<p>Given a string <code>s</code>, return <em>the sum of <strong>beauty</strong> of all of its substrings.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aabcb&quot;
<strong>Output:</strong> 5
<strong>Explanation: </strong>The substrings with non-zero beauty are [&quot;aab&quot;,&quot;aabc&quot;,&quot;aabcb&quot;,&quot;abcb&quot;,&quot;bcb&quot;], each with beauty equal to 1.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aabcbaa&quot;
<strong>Output:</strong> 17
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;=<sup> </sup>500</code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>


### ZH-CN:
<p>一个字符串的 <strong>美丽值</strong> 定义为：出现频率最高字符与出现频率最低字符的出现次数之差。</p>

<ul>
	<li>比方说，<code>"abaacc"</code> 的美丽值为 <code>3 - 1 = 2</code> 。</li>
</ul>

<p>给你一个字符串 <code>s</code> ，请你返回它所有子字符串的 <strong>美丽值</strong> 之和。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>s = "aabcb"
<b>输出：</b>5
<strong>解释：</strong>美丽值不为零的字符串包括 ["aab","aabc","aabcb","abcb","bcb"] ，每一个字符串的美丽值都为 1 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>s = "aabcbaa"
<b>输出：</b>17
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <=<sup> </sup>500</code></li>
	<li><code>s</code> 只包含小写英文字母。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/sum-of-beauty-of-all-substrings/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/sum-of-beauty-of-all-substrings/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 364 ms | 8.5 MB | 2022/12/11 15:30 |

```cpp

class Solution {
public:
    int beautySum(string s) {
        const int n = s.length();
        int ans = 0;
        for(int i = 0 ; i < n; i++){
            vector<int> cnt(26, 0);
            int maxVal = INT_MIN, minVal = INT_MAX;
            for(int j = i; j < n; j++){
                cnt[s[j] - 'a']++;
                for(int k = 0; k < 26; k++){
                    maxVal = max(maxVal, cnt[k]);
                    if(cnt[k] > 0) minVal = min(minVal, cnt[k]);
                }
                ans += maxVal - minVal;
                maxVal = INT_MIN;
                minVal = INT_MAX;
            }
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

