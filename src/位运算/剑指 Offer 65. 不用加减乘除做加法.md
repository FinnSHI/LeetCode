# [剑指 Offer 65. 不用加减乘除做加法](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

## 题目

写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。

 

```
示例:

输入: a = 1, b = 1
输出: 2
```

## 思路

不能用加减乘除，那我就用位运算、异或来做，诶嘿

### 知识补充

#### 负数补码表示法

- 正数是**源码表示法**，比如1的二进制是0000 0001

- 负数是**补码表示法**，即`源码表示法取反后+1`，比如 -1 怎么表示呢？
  - 1 的二进制是0000 0001
  - 取反变成 1111 1110
  - +1 变成 1111 1111
  - 则 -1 的二进制表示为 1111 1111

> 为什么用补码表示法？
>
> 计算机中只有加法器，负数用补码表示后，加法和减法都变成加法运算。

#### 异或运算 ^ 

两数相同为 0，不同为 1

- 任何数 x 与 0 异或都为 x

### 运算优先级

| 优先级 | 运算符                                           | 结合性   |
| ------ | ------------------------------------------------ | -------- |
| 1      | ()、[]、{}                                       | 从左向右 |
| 2      | !、+、-、~、++、--                               | 从右向左 |
| 3      | *、/、%                                          | 从左向右 |
| 4      | +、-                                             | 从左向右 |
| 5      | «、»、>>>                                        | 从左向右 |
| 6      | <、<=、>、>=、instanceof                         | 从左向右 |
| 7      | ==、!=                                           | 从左向右 |
| 8      | &                                                | 从左向右 |
| 9      | ^                                                | 从左向右 |
| 10     | \|                                               | 从左向右 |
| 11     | &&                                               | 从左向右 |
| 12     | \|\|                                             | 从左向右 |
| 13     | ?:                                               | 从右向左 |
| 14     | =、+=、-=、*=、/=、&=、\|=、^=、~=、«=、»=、>>>= | 从右向左 |

### 本题思路

- 两数每个位上的值进行相加运算：
  - 不需要进位的位进行异或运算^。
  - 需要进位的位只有两种情况，可以用与运算 & 进行判断
    - 两个数在该位的值都是1
    - 加上一个位的进位后，变成两个数为 1 的运算。



## 代码

```java
class Solution {
    public int add(int a, int b) {
        // 不需要进位的位相加：a ^ b
        // 需要进位的位相加，得到进位 carry = a & b << 1

        int carry = 1;
        while(carry != 0) {
            carry = (a & b) << 1;
            a = a ^ b;
            b = carry;    
        }

        return a;
    }
}
```



## 复杂度

时间复杂度：$O(1)$

空间复杂度：$O(1)$

