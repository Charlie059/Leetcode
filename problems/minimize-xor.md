
# 2429. Minimize XOR - 最小 XOR

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/Bit Manipulation-位运算-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two positive integers <code>num1</code> and <code>num2</code>, find the positive integer <code>x</code> such that:</p>

<ul>
	<li><code>x</code> has the same number of set bits as <code>num2</code>, and</li>
	<li>The value <code>x XOR num1</code> is <strong>minimal</strong>.</li>
</ul>

<p>Note that <code>XOR</code> is the bitwise XOR operation.</p>

<p>Return <em>the integer </em><code>x</code>. The test cases are generated such that <code>x</code> is <strong>uniquely determined</strong>.</p>

<p>The number of <strong>set bits</strong> of an integer is the number of <code>1</code>&#39;s in its binary representation.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num1 = 3, num2 = 5
<strong>Output:</strong> 3
<strong>Explanation:</strong>
The binary representations of num1 and num2 are 0011 and 0101, respectively.
The integer <strong>3</strong> has the same number of set bits as num2, and the value <code>3 XOR 3 = 0</code> is minimal.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num1 = 1, num2 = 12
<strong>Output:</strong> 3
<strong>Explanation:</strong>
The binary representations of num1 and num2 are 0001 and 1100, respectively.
The integer <strong>3</strong> has the same number of set bits as num2, and the value <code>3 XOR 1 = 2</code> is minimal.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num1, num2 &lt;= 10<sup>9</sup></code></li>
</ul>


### ZH-CN:
<p>给你两个正整数 <code>num1</code> 和 <code>num2</code> ，找出满足下述条件的整数 <code>x</code> ：</p>

<ul>
	<li><code>x</code> 的置位数和 <code>num2</code> 相同，且</li>
	<li><code>x XOR num1</code> 的值 <strong>最小</strong></li>
</ul>

<p>注意 <code>XOR</code> 是按位异或运算。</p>

<p>返回整数<em> </em><code>x</code> 。题目保证，对于生成的测试用例， <code>x</code> 是 <strong>唯一确定</strong> 的。</p>

<p>整数的 <strong>置位数</strong> 是其二进制表示中 <code>1</code> 的数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>num1 = 3, num2 = 5
<strong>输出：</strong>3
<strong>解释：</strong>
num1 和 num2 的二进制表示分别是 0011 和 0101 。
整数 <strong>3</strong> 的置位数与 num2 相同，且 <code>3 XOR 3 = 0</code> 是最小的。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>num1 = 1, num2 = 12
<strong>输出：</strong>3
<strong>解释：</strong>
num1 和 num2 的二进制表示分别是 0001 和 1100 。
整数 <strong>3</strong> 的置位数与 num2 相同，且 <code>3 XOR 1 = 2</code> 是最小的。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num1, num2 &lt;= 10<sup>9</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimize-xor/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/minimize-xor/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6 MB | 2022/10/01 23:25 |

```cpp

class Solution {
public:
    int countOnes(int num2){
         return __builtin_popcount(num2);
    }
    
    
    vector<int> getBits(int num1){
        vector<int> bits;
        while(num1){
            int a = num1 % 2;
            bits.emplace_back(a);
            num1 /= 2;
        }
        reverse(bits.begin(), bits.end());
        return bits;
    }
    
    int minimizeXor(int num1, int num2) {
        // count the numofbits
        vector<int> bits = getBits(num1);
        int n = bits.size();
        int m = countOnes(num2);
        
        string ans;

        
        for(int i = 0; i < n; i++){
            if(m > 0 && bits[i] == 1){
                ans += "1";
                m--;
            }else ans += "0";
        }
        
        // cout << ans << endl;
        // cout << m << endl;
    
        if(m > 0){
            for(int i = n - 1; i >= 0; i--){
                if(m > 0 && ans[i] == '0'){
                    ans[i] = '1';
                    m--;
                }
            }
        }
        
        
        if(m > 0){
            for(int i = 0; i < m; i++){
                ans = "1" + ans;
            }
        }
        // reverse(ans.begin(), ans.end());
        int res = 0;
        for(int i = ans.size() - 1; i >= 0 ; i--){
            res += (ans[i] - '0') * pow(2, ans.size() - i - 1);
        }
        
        
        return res;
    }
};

```
## My Notes - 我的笔记


No notes

