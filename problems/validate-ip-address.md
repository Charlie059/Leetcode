
# 468. Validate IP Address - 验证IP地址

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>queryIP</code>, return <code>&quot;IPv4&quot;</code> if IP is a valid IPv4 address, <code>&quot;IPv6&quot;</code> if IP is a valid IPv6 address or <code>&quot;Neither&quot;</code> if IP is not a correct IP of any type.</p>

<p><strong>A valid IPv4</strong> address is an IP in the form <code>&quot;x<sub>1</sub>.x<sub>2</sub>.x<sub>3</sub>.x<sub>4</sub>&quot;</code> where <code>0 &lt;= x<sub>i</sub> &lt;= 255</code> and <code>x<sub>i</sub></code> <strong>cannot contain</strong> leading zeros. For example, <code>&quot;192.168.1.1&quot;</code> and <code>&quot;192.168.1.0&quot;</code> are valid IPv4 addresses while <code>&quot;192.168.01.1&quot;</code>, <code>&quot;192.168.1.00&quot;</code>, and <code>&quot;192.168@1.1&quot;</code> are invalid IPv4 addresses.</p>

<p><strong>A valid IPv6</strong> address is an IP in the form <code>&quot;x<sub>1</sub>:x<sub>2</sub>:x<sub>3</sub>:x<sub>4</sub>:x<sub>5</sub>:x<sub>6</sub>:x<sub>7</sub>:x<sub>8</sub>&quot;</code> where:</p>

<ul>
	<li><code>1 &lt;= x<sub>i</sub>.length &lt;= 4</code></li>
	<li><code>x<sub>i</sub></code> is a <strong>hexadecimal string</strong> which may contain digits, lowercase English letter (<code>&#39;a&#39;</code> to <code>&#39;f&#39;</code>) and upper-case English letters (<code>&#39;A&#39;</code> to <code>&#39;F&#39;</code>).</li>
	<li>Leading zeros are allowed in <code>x<sub>i</sub></code>.</li>
</ul>

<p>For example, &quot;<code>2001:0db8:85a3:0000:0000:8a2e:0370:7334&quot;</code> and &quot;<code>2001:db8:85a3:0:0:8A2E:0370:7334&quot;</code> are valid IPv6 addresses, while &quot;<code>2001:0db8:85a3::8A2E:037j:7334&quot;</code> and &quot;<code>02001:0db8:85a3:0000:0000:8a2e:0370:7334&quot;</code> are invalid IPv6 addresses.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> queryIP = &quot;172.16.254.1&quot;
<strong>Output:</strong> &quot;IPv4&quot;
<strong>Explanation:</strong> This is a valid IPv4 address, return &quot;IPv4&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> queryIP = &quot;2001:0db8:85a3:0:0:8A2E:0370:7334&quot;
<strong>Output:</strong> &quot;IPv6&quot;
<strong>Explanation:</strong> This is a valid IPv6 address, return &quot;IPv6&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> queryIP = &quot;256.256.256.256&quot;
<strong>Output:</strong> &quot;Neither&quot;
<strong>Explanation:</strong> This is neither a IPv4 address nor a IPv6 address.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>queryIP</code> consists only of English letters, digits and the characters <code>&#39;.&#39;</code> and <code>&#39;:&#39;</code>.</li>
</ul>


### ZH-CN:
<p>给定一个字符串&nbsp;<code>queryIP</code>。如果是有效的 IPv4 地址，返回 <code>"IPv4"</code> ；如果是有效的 IPv6 地址，返回 <code>"IPv6"</code> ；如果不是上述类型的 IP 地址，返回 <code>"Neither"</code> 。</p>

<p><strong>有效的IPv4地址</strong> 是 <code>“x1.x2.x3.x4”</code> 形式的IP地址。 其中&nbsp;<code>0 &lt;= x<sub>i</sub>&nbsp;&lt;= 255</code>&nbsp;且&nbsp;<code>x<sub>i</sub></code>&nbsp;<strong>不能包含</strong> 前导零。例如:&nbsp;<code>“192.168.1.1”</code>&nbsp;、 <code>“192.168.1.0”</code> 为有效IPv4地址， <code>“192.168.01.1”</code> 为无效IPv4地址; <code>“192.168.1.00”</code> 、 <code>“192.168@1.1”</code> 为无效IPv4地址。</p>

<p><strong>一个有效的IPv6地址&nbsp;</strong>是一个格式为<code>“x1:x2:x3:x4:x5:x6:x7:x8”</code> 的IP地址，其中:</p>

<ul>
	<li><code>1 &lt;= x<sub>i</sub>.length &lt;= 4</code></li>
	<li><code>x<sub>i</sub></code>&nbsp;是一个 <strong>十六进制字符串</strong> ，可以包含数字、小写英文字母( <code>'a'</code> 到 <code>'f'</code> )和大写英文字母( <code>'A'</code> 到 <code>'F'</code> )。</li>
	<li>在&nbsp;<code>x<sub>i</sub></code>&nbsp;中允许前导零。</li>
</ul>

<p>例如 <code>"2001:0db8:85a3:0000:0000:8a2e:0370:7334"</code> 和 <code>"2001:db8:85a3:0:0:8A2E:0370:7334"</code> 是有效的 IPv6 地址，而 <code>"2001:0db8:85a3::8A2E:037j:7334"</code> 和 <code>"02001:0db8:85a3:0000:0000:8a2e:0370:7334"</code> 是无效的 IPv6 地址。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>queryIP = "172.16.254.1"
<strong>输出：</strong>"IPv4"
<strong>解释：</strong>有效的 IPv4 地址，返回 "IPv4"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>queryIP = "2001:0db8:85a3:0:0:8A2E:0370:7334"
<strong>输出：</strong>"IPv6"
<strong>解释：</strong>有效的 IPv6 地址，返回 "IPv6"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>queryIP = "256.256.256.256"
<strong>输出：</strong>"Neither"
<strong>解释：</strong>既不是 IPv4 地址，又不是 IPv6 地址
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>queryIP</code> 仅由英文字母，数字，字符 <code>'.'</code> 和 <code>':'</code> 组成。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/validate-ip-address/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/validate-ip-address/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 296 ms | 46 MB | 2022/03/08 10:10 |

```cpp

class Solution {
public:
// 255.1.1.1
    string validIPAddress(string queryIP) {
        regex ipv4("(([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5]).){3}([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])");
        regex ipv6("([0-9a-fA-F]{1,4}\\:){7}[0-9a-fA-F]{1,4}");
        if (regex_match(queryIP, ipv4)) return "IPv4";
        else if (regex_match(queryIP, ipv6)) return "IPv6";
        else return "Neither";
    }
};

```
## My Notes - 我的笔记


No notes

