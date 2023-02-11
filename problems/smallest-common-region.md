
# 1257. Smallest Common Region - 最小公共区域

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Tree-树-blue.svg">   <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given some lists of <code>regions</code> where the first region of each list includes all other regions in that list.</p>

<p>Naturally, if a region <code>x</code> contains another region <code>y</code> then <code>x</code> is bigger than <code>y</code>. Also, by definition, a region <code>x</code> contains itself.</p>

<p>Given two regions: <code>region1</code> and <code>region2</code>, return <em>the smallest region that contains both of them</em>.</p>

<p>If you are given regions <code>r1</code>, <code>r2</code>, and <code>r3</code> such that <code>r1</code> includes <code>r3</code>, it is guaranteed there is no <code>r2</code> such that <code>r2</code> includes <code>r3</code>.</p>

<p>It is guaranteed the smallest region exists.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:
</strong>regions = [[&quot;Earth&quot;,&quot;North America&quot;,&quot;South America&quot;],
[&quot;North America&quot;,&quot;United States&quot;,&quot;Canada&quot;],
[&quot;United States&quot;,&quot;New York&quot;,&quot;Boston&quot;],
[&quot;Canada&quot;,&quot;Ontario&quot;,&quot;Quebec&quot;],
[&quot;South America&quot;,&quot;Brazil&quot;]],
region1 = &quot;Quebec&quot;,
region2 = &quot;New York&quot;
<strong>Output:</strong> &quot;North America&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> regions = [[&quot;Earth&quot;, &quot;North America&quot;, &quot;South America&quot;],[&quot;North America&quot;, &quot;United States&quot;, &quot;Canada&quot;],[&quot;United States&quot;, &quot;New York&quot;, &quot;Boston&quot;],[&quot;Canada&quot;, &quot;Ontario&quot;, &quot;Quebec&quot;],[&quot;South America&quot;, &quot;Brazil&quot;]], region1 = &quot;Canada&quot;, region2 = &quot;South America&quot;
<strong>Output:</strong> &quot;Earth&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= regions.length &lt;= 10<sup>4</sup></code></li>
	<li><code>2 &lt;= regions[i].length &lt;= 20</code></li>
	<li><code>1 &lt;= regions[i][j].length, region1.length, region2.length &lt;= 20</code></li>
	<li><code>region1 != region2</code></li>
	<li><code>regions[i][j]</code>, <code>region1</code>, and <code>region2</code> consist of English letters.</li>
</ul>


### ZH-CN:
<p>给你一些区域列表&nbsp;<code>regions</code> ，每个列表的第一个区域都包含这个列表内所有其他区域。</p>

<p>很自然地，如果区域&nbsp;<code>X</code> 包含区域&nbsp;<code>Y</code> ，那么区域&nbsp;<code>X</code> &nbsp;比区域&nbsp;<code>Y</code> 大。</p>

<p>给定两个区域&nbsp;<code>region1</code>&nbsp;和&nbsp;<code>region2</code> ，找到同时包含这两个区域的&nbsp;<strong>最小&nbsp;</strong>区域。</p>

<p>如果区域列表中&nbsp;<code>r1</code>&nbsp;包含&nbsp;<code>r2</code>&nbsp;和&nbsp;<code>r3</code> ，那么数据保证&nbsp;<code>r2</code> 不会包含&nbsp;<code>r3</code>&nbsp;。</p>

<p>数据同样保证最小公共区域一定存在。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：
</strong>regions = [[&quot;Earth&quot;,&quot;North America&quot;,&quot;South America&quot;],
[&quot;North America&quot;,&quot;United States&quot;,&quot;Canada&quot;],
[&quot;United States&quot;,&quot;New York&quot;,&quot;Boston&quot;],
[&quot;Canada&quot;,&quot;Ontario&quot;,&quot;Quebec&quot;],
[&quot;South America&quot;,&quot;Brazil&quot;]],
region1 = &quot;Quebec&quot;,
region2 = &quot;New York&quot;
<strong>输出：</strong>&quot;North America&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= regions.length &lt;= 10^4</code></li>
	<li><code>region1 != region2</code></li>
	<li>所有字符串只包含英文字母和空格，且最多只有&nbsp;20 个字母。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/smallest-common-region/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/smallest-common-region/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 64 ms | 34.4 MB | 2022/10/03 9:59 |

```cpp

class Solution {
public:
    string findSmallestRegion(vector<vector<string>>& regions, string region1, string region2) {
        const int m = regions.size();
        unordered_map<string, string> hm;
        
        for(int i = 0; i < m; i++){
            for(int j = 1; j < regions[i].size(); j++){
                hm[regions[i][j]] = regions[i][0];
            }
        }

        unordered_set<string> hs;
        while(hm.count(region1)){
            hs.emplace(region1);
            region1 = hm[region1];
        }
hs.emplace(region1);
        while(true){
            if(hs.count(region2)) return region2;
            region2 = hm[region2];
        }
        return nullptr;
    }
};

```
## My Notes - 我的笔记


No notes

