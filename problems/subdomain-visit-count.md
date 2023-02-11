
# 811. Subdomain Visit Count - 子域名访问计数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Counting-计数-blue.svg">  


## Description - 题目描述

### EN:
<p>A website domain <code>&quot;discuss.leetcode.com&quot;</code> consists of various subdomains. At the top level, we have <code>&quot;com&quot;</code>, at the next level, we have <code>&quot;leetcode.com&quot;</code>&nbsp;and at the lowest level, <code>&quot;discuss.leetcode.com&quot;</code>. When we visit a domain like <code>&quot;discuss.leetcode.com&quot;</code>, we will also visit the parent domains <code>&quot;leetcode.com&quot;</code> and <code>&quot;com&quot;</code> implicitly.</p>

<p>A <strong>count-paired domain</strong> is a domain that has one of the two formats <code>&quot;rep d1.d2.d3&quot;</code> or <code>&quot;rep d1.d2&quot;</code> where <code>rep</code> is the number of visits to the domain and <code>d1.d2.d3</code> is the domain itself.</p>

<ul>
	<li>For example, <code>&quot;9001 discuss.leetcode.com&quot;</code> is a <strong>count-paired domain</strong> that indicates that <code>discuss.leetcode.com</code> was visited <code>9001</code> times.</li>
</ul>

<p>Given an array of <strong>count-paired domains</strong> <code>cpdomains</code>, return <em>an array of the <strong>count-paired domains</strong> of each subdomain in the input</em>. You may return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> cpdomains = [&quot;9001 discuss.leetcode.com&quot;]
<strong>Output:</strong> [&quot;9001 leetcode.com&quot;,&quot;9001 discuss.leetcode.com&quot;,&quot;9001 com&quot;]
<strong>Explanation:</strong> We only have one website domain: &quot;discuss.leetcode.com&quot;.
As discussed above, the subdomain &quot;leetcode.com&quot; and &quot;com&quot; will also be visited. So they will all be visited 9001 times.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> cpdomains = [&quot;900 google.mail.com&quot;, &quot;50 yahoo.com&quot;, &quot;1 intel.mail.com&quot;, &quot;5 wiki.org&quot;]
<strong>Output:</strong> [&quot;901 mail.com&quot;,&quot;50 yahoo.com&quot;,&quot;900 google.mail.com&quot;,&quot;5 wiki.org&quot;,&quot;5 org&quot;,&quot;1 intel.mail.com&quot;,&quot;951 com&quot;]
<strong>Explanation:</strong> We will visit &quot;google.mail.com&quot; 900 times, &quot;yahoo.com&quot; 50 times, &quot;intel.mail.com&quot; once and &quot;wiki.org&quot; 5 times.
For the subdomains, we will visit &quot;mail.com&quot; 900 + 1 = 901 times, &quot;com&quot; 900 + 50 + 1 = 951 times, and &quot;org&quot; 5 times.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= cpdomain.length &lt;= 100</code></li>
	<li><code>1 &lt;= cpdomain[i].length &lt;= 100</code></li>
	<li><code>cpdomain[i]</code> follows either the <code>&quot;rep<sub>i</sub> d1<sub>i</sub>.d2<sub>i</sub>.d3<sub>i</sub>&quot;</code> format or the <code>&quot;rep<sub>i</sub> d1<sub>i</sub>.d2<sub>i</sub>&quot;</code> format.</li>
	<li><code>rep<sub>i</sub></code> is an integer in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>d1<sub>i</sub></code>, <code>d2<sub>i</sub></code>, and <code>d3<sub>i</sub></code> consist of lowercase English letters.</li>
</ul>


### ZH-CN:
<p>网站域名 <code>"discuss.leetcode.com"</code> 由多个子域名组成。顶级域名为 <code>"com"</code> ，二级域名为 <code>"leetcode.com"</code> ，最低一级为 <code>"discuss.leetcode.com"</code> 。当访问域名 <code>"discuss.leetcode.com"</code> 时，同时也会隐式访问其父域名 <code>"leetcode.com" </code>以及 <code>"com"</code> 。</p>

<p><strong>计数配对域名</strong> 是遵循 <code>"rep d1.d2.d3"</code> 或 <code>"rep d1.d2"</code> 格式的一个域名表示，其中 <code>rep</code> 表示访问域名的次数，<code>d1.d2.d3</code> 为域名本身。</p>

<ul>
	<li>例如，<code>"9001 discuss.leetcode.com"</code> 就是一个 <strong>计数配对域名</strong> ，表示 <code>discuss.leetcode.com</code> 被访问了 <code>9001</code> 次。</li>
</ul>

<p>给你一个<strong> 计数配对域名 </strong>组成的数组 <code>cpdomains</code> ，解析得到输入中每个子域名对应的&nbsp;<strong>计数配对域名</strong> ，并以数组形式返回。可以按 <strong>任意顺序</strong> 返回答案。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>cpdomains = ["9001 discuss.leetcode.com"]
<strong>输出：</strong>["9001 leetcode.com","9001 discuss.leetcode.com","9001 com"]
<strong>解释：</strong>例子中仅包含一个网站域名："discuss.leetcode.com"。
按照前文描述，子域名 "leetcode.com" 和 "com" 都会被访问，所以它们都被访问了 9001 次。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>cpdomains = ["900 google.mail.com", "50 yahoo.com", "1 intel.mail.com", "5 wiki.org"]
<strong>输出：</strong>["901 mail.com","50 yahoo.com","900 google.mail.com","5 wiki.org","5 org","1 intel.mail.com","951 com"]
<strong>解释：</strong>按照前文描述，会访问 "google.mail.com" 900 次，"yahoo.com" 50 次，"intel.mail.com" 1 次，"wiki.org" 5 次。
而对于父域名，会访问 "mail.com" 900 + 1 = 901 次，"com" 900 + 50 + 1 = 951 次，和 "org" 5 次。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= cpdomain.length &lt;= 100</code></li>
	<li><code>1 &lt;= cpdomain[i].length &lt;= 100</code></li>
	<li><code>cpdomain[i]</code> 会遵循 <code>"rep<sub>i</sub> d1<sub>i</sub>.d2<sub>i</sub>.d3<sub>i</sub>"</code> 或 <code>"rep<sub>i</sub> d1<sub>i</sub>.d2<sub>i</sub>"</code> 格式</li>
	<li><code>rep<sub>i</sub></code> 是范围 <code>[1, 10<sup>4</sup>]</code> 内的一个整数</li>
	<li><code>d1<sub>i</sub></code>、<code>d2<sub>i</sub></code> 和 <code>d3<sub>i</sub></code> 由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/subdomain-visit-count/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/subdomain-visit-count/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 28 ms | 11.4 MB | 2022/10/06 11:50 |

```cpp

class Solution {
public:
    unordered_map<string, int> hm;
    void spilt2Add(string& s){
        // Spilt the first value
        int val = stoi(s);
        // Get the rest of string
        s = s.substr(to_string(val).size() + 1);
        int pos = 0;
        while((pos = s.find_first_of(".")) != string::npos){
            hm[s] += val;
            // cout << s << endl;
            s = s.substr(pos + 1);         
        }
        hm[s] += val;
        // cout << s << endl;
    }
    vector<string> subdomainVisits(vector<string>& cpdomains) {
        

        const int n = cpdomains.size();
        for(int i = 0; i < n; i++) spilt2Add(cpdomains[i]);
        
        vector<string> ans;
        for(auto i: hm){
            string tmp = to_string(i.second) + " " + i.first;
            ans.emplace_back(tmp);
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

