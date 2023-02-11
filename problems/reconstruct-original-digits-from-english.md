
# 423. Reconstruct Original Digits from English - 从英文中重建数字

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code> containing an out-of-order English representation of digits <code>0-9</code>, return <em>the digits in <strong>ascending</strong> order</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> s = "owoztneoer"
<strong>Output:</strong> "012"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> s = "fviefuro"
<strong>Output:</strong> "45"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is one of the characters <code>[&quot;e&quot;,&quot;g&quot;,&quot;f&quot;,&quot;i&quot;,&quot;h&quot;,&quot;o&quot;,&quot;n&quot;,&quot;s&quot;,&quot;r&quot;,&quot;u&quot;,&quot;t&quot;,&quot;w&quot;,&quot;v&quot;,&quot;x&quot;,&quot;z&quot;]</code>.</li>
	<li><code>s</code> is <strong>guaranteed</strong> to be valid.</li>
</ul>


### ZH-CN:
<p>给你一个字符串 <code>s</code> ，其中包含字母顺序打乱的用英文单词表示的若干数字（<code>0-9</code>）。按 <strong>升序</strong> 返回原始的数字。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "owoztneoer"
<strong>输出：</strong>"012"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "fviefuro"
<strong>输出：</strong>"45"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> 为 <code>["e","g","f","i","h","o","n","s","r","u","t","w","v","x","z"]</code> 这些字符之一</li>
	<li><code>s</code> 保证是一个符合题目要求的字符串</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/reconstruct-original-digits-from-english/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/reconstruct-original-digits-from-english/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 12 ms | 8.6 MB | 2022/07/18 15:22 |

```cpp

class Solution {
public:
    string originalDigits(string s) {
        //zero, one, two, three, four, five, six, seven, eight, nine
        //"owoztneoer" -> o: 3, w: 1, z: 1, t: 1, n: 1, e: 2, r: 1

        unordered_map<char, int> mp;

        for(char c: s){
            mp[c]++;
        }

        vector<int> cnt(10);

        cnt[0] = mp['z'];
        cnt[2] = mp['w'];
        cnt[4] = mp['u'];
        cnt[6] = mp['x'];
        cnt[8] = mp['g'];

        cnt[3] = mp['h'] - cnt[8];
        cnt[5] = mp['f'] - cnt[4];
        cnt[7] = mp['v'] - cnt[5];

        cnt[1] = mp['o'] - cnt[0] - cnt[2] - cnt[4];
        cnt[9] = mp['i'] - cnt[5] - cnt[6] - cnt[8];

        string ans;
        for(int i = 0; i < 10; i++){
            while(cnt[i] > 0){
                ans += char(i + '0');
                cnt[i]--;
            }
        }

        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

