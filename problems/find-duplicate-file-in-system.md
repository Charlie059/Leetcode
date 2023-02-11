
# 609. Find Duplicate File in System - 在系统中查找重复文件

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a list <code>paths</code> of directory info, including the directory path, and all the files with contents in this directory, return <em>all the duplicate files in the file system in terms of their paths</em>. You may return the answer in <strong>any order</strong>.</p>

<p>A group of duplicate files consists of at least two files that have the same content.</p>

<p>A single directory info string in the input list has the following format:</p>

<ul>
	<li><code>&quot;root/d1/d2/.../dm f1.txt(f1_content) f2.txt(f2_content) ... fn.txt(fn_content)&quot;</code></li>
</ul>

<p>It means there are <code>n</code> files <code>(f1.txt, f2.txt ... fn.txt)</code> with content <code>(f1_content, f2_content ... fn_content)</code> respectively in the directory &quot;<code>root/d1/d2/.../dm&quot;</code>. Note that <code>n &gt;= 1</code> and <code>m &gt;= 0</code>. If <code>m = 0</code>, it means the directory is just the root directory.</p>

<p>The output is a list of groups of duplicate file paths. For each group, it contains all the file paths of the files that have the same content. A file path is a string that has the following format:</p>

<ul>
	<li><code>&quot;directory_path/file_name.txt&quot;</code></li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> paths = ["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)","root 4.txt(efgh)"]
<strong>Output:</strong> [["root/a/2.txt","root/c/d/4.txt","root/4.txt"],["root/a/1.txt","root/c/3.txt"]]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> paths = ["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)"]
<strong>Output:</strong> [["root/a/2.txt","root/c/d/4.txt"],["root/a/1.txt","root/c/3.txt"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= paths.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= paths[i].length &lt;= 3000</code></li>
	<li><code>1 &lt;= sum(paths[i].length) &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>paths[i]</code> consist of English letters, digits, <code>&#39;/&#39;</code>, <code>&#39;.&#39;</code>, <code>&#39;(&#39;</code>, <code>&#39;)&#39;</code>, and <code>&#39; &#39;</code>.</li>
	<li>You may assume no files or directories share the same name in the same directory.</li>
	<li>You may assume each given directory info represents a unique directory. A single blank space separates the directory path and file info.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>Imagine you are given a real file system, how will you search files? DFS or BFS?</li>
	<li>If the file content is very large (GB level), how will you modify your solution?</li>
	<li>If you can only read the file by 1kb each time, how will you modify your solution?</li>
	<li>What is the time complexity of your modified solution? What is the most time-consuming part and memory-consuming part of it? How to optimize?</li>
	<li>How to make sure the duplicated files you find are not false positive?</li>
</ul>


### ZH-CN:
<p>给你一个目录信息列表&nbsp;<code>paths</code> ，包括目录路径，以及该目录中的所有文件及其内容，请你按路径返回文件系统中的所有重复文件。答案可按 <strong>任意顺序</strong> 返回。</p>

<p>一组重复的文件至少包括 <strong>两个 </strong>具有完全相同内容的文件。</p>

<p><strong>输入 </strong>列表中的单个目录信息字符串的格式如下：</p>

<ul>
	<li><code>"root/d1/d2/.../dm f1.txt(f1_content) f2.txt(f2_content) ... fn.txt(fn_content)"</code></li>
</ul>

<p>这意味着，在目录&nbsp;<code>root/d1/d2/.../dm</code>&nbsp;下，有 <code>n</code> 个文件 ( <code>f1.txt</code>,&nbsp;<code>f2.txt</code>&nbsp;...&nbsp;<code>fn.txt</code> ) 的内容分别是 ( <code>f1_content</code>,&nbsp;<code>f2_content</code>&nbsp;...&nbsp;<code>fn_content</code> ) 。注意：<code>n &gt;= 1</code> 且 <code>m &gt;= 0</code> 。如果 <code>m = 0</code> ，则表示该目录是根目录。</p>

<p><strong>输出 </strong>是由 <strong>重复文件路径组</strong> 构成的列表。其中每个组由所有具有相同内容文件的文件路径组成。文件路径是具有下列格式的字符串：</p>

<ul>
	<li><code>"directory_path/file_name.txt"</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>paths = ["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)","root 4.txt(efgh)"]
<strong>输出：</strong>[["root/a/2.txt","root/c/d/4.txt","root/4.txt"],["root/a/1.txt","root/c/3.txt"]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>paths = ["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)"]
<strong>输出：</strong>[["root/a/2.txt","root/c/d/4.txt"],["root/a/1.txt","root/c/3.txt"]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= paths.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= paths[i].length &lt;= 3000</code></li>
	<li><code>1 &lt;= sum(paths[i].length) &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>paths[i]</code> 由英文字母、数字、字符 <code>'/'</code>、<code>'.'</code>、<code>'('</code>、<code>')'</code> 和 <code>' '</code> 组成</li>
	<li>你可以假设在同一目录中没有任何文件或目录共享相同的名称。</li>
	<li>你可以假设每个给定的目录信息代表一个唯一的目录。目录路径和文件信息用单个空格分隔。</li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶：</strong></p>

<ul>
	<li>假设您有一个真正的文件系统，您将如何搜索文件？广度搜索还是宽度搜索？</li>
	<li>如果文件内容非常大（GB级别），您将如何修改您的解决方案？</li>
	<li>如果每次只能读取 1 kb 的文件，您将如何修改解决方案？</li>
	<li>修改后的解决方案的时间复杂度是多少？其中最耗时的部分和消耗内存的部分是什么？如何优化？</li>
	<li>如何确保您发现的重复文件不是误报？</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/find-duplicate-file-in-system/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/find-duplicate-file-in-system/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 108 ms | 49.4 MB | 2022/08/24 10:11 |

```cpp

class Solution {
private:
    std::pair<string, string> getFileNameAndContent(string & s){
        string fileName, content;
        int pos = s.find("(");
        fileName = s.substr(0, pos);
        content = s.substr(pos + 1);
        return std::make_pair(fileName, content);
    }
    vector<string> splitString(string & s){
        vector<string> ans;
        stringstream ss(s);
        string tmp;

        while(ss >> tmp) ans.emplace_back(tmp);
        return ans;
    }
public:
    vector<vector<string>> findDuplicate(vector<string>& paths) {
        const int n = paths.size();
        unordered_map<string, vector<string>> hm;

        for(int i = 0; i < n; i++){
            string curr = paths[i];
            vector<string> splitStr = splitString(curr);
            string address = splitStr[0];
            for(int j = 1; j < splitStr.size(); j++){
                auto p = getFileNameAndContent(splitStr[j]);
                hm[p.second].emplace_back(address + "/" + p.first);
            }
        }

        vector<vector<string>> ans;
        for(auto it: hm) if(it.second.size() > 1) ans.emplace_back(it.second);
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

