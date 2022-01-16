# 算法知识总结

## 零、取值范围

数字的取值范围：

* Int8, 等于**Byte**, 占1个字节，即8位。$(-2^{7}, 2^{7}-1)$
* Int16, 等于**short**, 占2个字节，即16位。 $(-2^{15},2^{15}-1)$,即$-32768$~$32767$
* Int32, 等于**int**, 占4字节，即32位：$(-2^{31}, 2^{31}-1)$。即$$-2147483648$~$2147483647$
* Int64, 等于**long**, 占8个字节, 即64位。$(-2^{63}, 2^{63}-1)$, -9223372036854775808 9223372036854775807
* **float**，32位
* **double**，64 位



## 一、复杂度

### 时间复杂度

常见时间复杂度排序：

![image-20210913180516076](E:\Typora_Documents\Data Structure\imgs\数据结构.assets\image-20210913180516076.png)

<img src="E:\Typora_Documents\Data Structure\imgs\数据结构.assets\image-20210924154023676.png" alt="image-20210924154023676" style="zoom:50%;" />



#### 选择排序的时间复杂度

以选择排序为例求时间复杂度。

选择排序：

1. 在$0$ ~ $N-1$内找到最小值，放在第0个位置。
2. 在$1$ ~ $N-1$内找到最小值，放在第1个位置。
3. 在$2$ ~ $N-1$内找到最小值，放在第2个位置。
4. ...
5. 在$N-2$ ~ $N-1$内找到最小值，放在第N-2个位置。

计算时间复杂度：$(N-1)+(N-2)+...+1=N×(N-1)/2$

时间复杂度为：$O(n^2)$



### 空间复杂度

分析输入和程序之外的**额外空间**。



## 二、动态规划

用于找出最优方法。

1. 穷举法/暴力搜索
2. 记忆化搜索/剪枝
3. 改写成迭代

### 1. 示例：

num = [1, 5, 2, 4, 3]; 找出连续增长的最长的子数组长度。

* #### 暴力search

<img src="E:\Typora_Documents\Data Structure\imgs\数据结构.assets\image-20210924153049430.png" alt="image-20210924153049430" style="zoom:33%;" />

​	然后分别从5，2，4，3出发....

​	存在大量重复运算，所以时间复杂度很高。

* #### 动态规划



## 三、分治算法

分治算法的基本思想是将一个规模为N的问题分解为K个规模较小的子问题，这些子问题相互独立且与原问题性质相同。求出子问题的解，就可得到原问题的解。即一种分目标完成程序算法，简单问题可用二分法完成。



## 四、java中队列

队列

1. Java中Queue接口由LinkedList实现。

   ```java
   Queue<TreeNode> queue = new LinkedList<>();
   ```

![](https://raw.githubusercontent.com/FinnSHI/PictureBed/main/imgs/202111081049958.png)

<br/>

<br/>

# 字符串

## 知识点总结



## 剑指Offer

### [剑指 Offer 44. 数字序列中某一位的数字](https://leetcode-cn.com/problems/shu-zi-xu-lie-zhong-mou-yi-wei-de-shu-zi-lcof/)

#### 题目

数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从下标0开始计数）是5，第13位是1，第19位是4，等等。

请写一个函数，求任意第n位对应的数字。

#### 示例

```
输入：n = 3
输出：3
```

```
输入：n = 11
输出：0
```

#### 思路

count是所有数字列出后的总位数

| number  |       start       |       digit       |      count      |
| :-----: | :---------------: | :---------------: | :-------------: |
|   1-9   |         1         |         1         |     $1×1×9$     |
|  10-99  |        10         |         2         |    $10×2×9$     |
| 100-999 |        100        |         3         |    $100×3×9$    |
|   ...   |        ...        |        ...        |       ...       |
|   ...   | start = start *10 | digit = digit + 1 | $start×digit×9$ |

1. 确定n所在的数字是几位的：digit
2. 确定n所在的数字：num
3. 确定n所在数字的第几位：res

------

### [剑指 Offer 50. 第一个只出现一次的字符](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

#### 题目

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

#### 示例

```
输入：s = "abaccdeff"
输出：'b'

输入：s = "" 
输出：' '
```

#### 思路

String 变成 char 数组 ——> s.toCharArray()

</br>

</br>

# 数组

## 知识点总结

### toArray

1. ArrayList转换成String数组可以用

   `list.toArray(new String[0])`



### 异或

#### 规则

符号：^

运算：相同为0，不同为1

```
0 ^ 0 = 0
0 ^ 1 = 1
1 ^ 0 = 1
1 ^ 1 = 0


= a⊕a⊕b⊕b⊕...⊕x
= 0⊕0⊕...⊕x
= x

1⊕6 = 7 (0001 ^ 0110 = 0111)
```

> 运算律
>
> - **一个值与自身的运算，总是为 false。**
>   - x ^ x = 0
> - **一个值与 0 的运算，总是等于其本身。**
>   - x ^ 0 = x
> - **可交换性**
>   - x ^ y = y ^ x
> - **结合性**
>   - x ^ (y ^ z) = (x ^ y) ^ z

#### 相关题目

1. [剑指 Offer 56 - I. 数组中数字出现的次数](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)



### 有限状态机

#### 图示

<img src="https://pic.leetcode-cn.com/0a7ea5bca055b095673620d8bb4c98ef6c610a22f999294ed11ae35d43621e93-Picture3.png" alt="Picture3.png" style="zoom:50%;" />

#### 状态转移表

<img src="https://pic.leetcode-cn.com/f75d89219ad93c69757b187c64784b4c7a57dce7911884fe82f14073d654d32f-Picture4.png" alt="Picture4.png" style="zoom:50%;" />

#### 相关题目

1. [剑指 Offer 56 - II. 数组中数字出现的次数 II](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)



## 剑指Offer

### [剑指 Offer 03. 数组中重复的数字](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

#### 题目

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

#### 示例

```
输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
```

#### 思路

对于0~n-1的数字：

​	——如果没有重复的数字，则数组第$i$个位置保存的就是$i$。

​	——如果出现重复的数字，那就扫描每个位置上的值$val$，并和$nums[val]$上的值交换（0和$nums[0]$的值交换）。如果$val$和$nums[val]$值相等，就是重复的元素。

------

### [剑指 Offer 04. 二维数组中的查找](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)

#### 题目

在一个 n * m的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

#### 示例

```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
] 

给定 target = 5，返回 true。
给定 target = 20，返回 false。
```

#### 思路

从右上角看的话，这就是个Binary Search Tree（有序二叉树）。

如果数组为空，直接返回false。

​	从右上角$matrix[0][j]$开始找。

​		——如果$matrix[0][j]$=$target$，那就没什么好说的了，直接return true。

​		——如果$matrix[0][j]$<$target$，那么排除第0行，从$matrix[1][j]$继续找。

​		——如果$matrix[0][j]$>$target$，则排除第j列（因为j列的值肯定都大于$target$）。



------

### [剑指 Offer 05. 替换空格](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)

#### 题目

请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。。

#### 示例

```
输入：s = "We are happy."
输出："We%20are%20happy."
```

#### 思路

Java直接用StringBuilder遍历一次就行了。 搞那么麻烦干嘛。





------

### [剑指 Offer 15. 二进制中1的个数](https://leetcode-cn.com/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)

#### 题目

编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为 汉明重量）。

提示：

请注意，在某些语言（如 Java）中，没有无符号整数类型。在这种情况下，输入和输出都将被指定为有符号整数类型，并且不应影响您的实现，因为**无论整数是有符号的还是无符号的，其内部的二进制表示形式都是相同的**。
在 Java 中，编译器使用 二进制补码 记法来表示有符号整数。因此，在上面的 示例 3 中，输入表示有符号整数 -3。

#### 示例

```
输入：n = 11 (控制台输入 00000000000000000000000000001011)
输出：3
解释：输入的二进制串 00000000000000000000000000001011 中，共有三位为 '1'。
```

```
输入：n = 128 (控制台输入 00000000000000000000000010000000)
输出：1
解释：输入的二进制串 00000000000000000000000010000000 中，共有一位为 '1'。
```

```
输入：n = 4294967293 (控制台输入 11111111111111111111111111111101，部分语言中 n = -3）
输出：31
解释：输入的二进制串 11111111111111111111111111111101 中，共有 31 位为 '1'。
```

#### 思路

##### 方法一：

我们可以直接循环检查给定整数 $n$ 的二进制位的每一位是否为 1。

具体方法是：将$n$和$2^i$比较

* 如果第i位是0， 则结果是0。
* 如果第i位不是0，则结果是$2^i$（非0）。

**时间复杂度：$O(n)$**

**空间复杂度：$O(1)$**



##### 方法二(降低时间复杂度)：

**位运算优化**

观察这个运算：$n$&$(n - 1)$，其预算结果恰为把 $n$ 的二进制位中的最低位的 1变为 0 之后的结果。

![image-20211008164933420](E:\Typora_Documents\Data Structure\imgs\剑指Offer刷题笔记.assets\image-20211008164933420.png)

所以只要不断比较$n$&$(n - 1)$，直到$n$变成0。

所以$n$有多少个1，就进行多少次运算。

```java

public class Solution {
    public int hammingWeight(int n) {
        int ret = 0;
        while (n != 0) {
            n &= n - 1;
            ret++;
        }
        return ret;
    }
}
```



<font color="red">???时间复杂度：$O(logn)$。循环次数等于 n 的二进制位中 1 的个数，**最坏情况下 n 的二进制位全部为 1。我们需要循环 $logn$ 次**。???</font>

空间复杂度：$O(1)$



------

### [剑指 Offer 17. 打印从1到最大的n位数](https://leetcode-cn.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

#### 题目

输入数字 `n`，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。

#### 示例

```
输入: n = 1
输出: [1,2,3,4,5,6,7,8,9]
```

#### 思路

##### 不考虑越界的情况

设$end$为最后一个数，则$end=10^n-1$

所以循环打印$1$~$10^n$的数就行了。

##### 考虑大数越界的情况——String字符串

首先，数字的取值范围：

* Int8, 等于Byte, 占1个字节，即8位。$(-2^{7}, 2^{7}-1)$
* Int16, 等于short, 占2个字节，即16位。 $(-2^{15},2^{15}-1)$,即$-32768$~$32767$
* Int32, 等于int, 占4字节，即32位：$(-2^{31}, 2^{31}-1)$。即$$-2147483648$~$2147483647$
* Int64, 等于long, 占8个字节, 即64位。$(-2^{63}, 2^{63}-1)$, -9223372036854775808 9223372036854775807
* float，32位
* double，64 位

开始解决大数越界的问题：**用String字符串来解决**

1. 生成数字的字符串集。

2. 递归生成全排列:

   * 基于**分治算法**的思想，先固定高位，向低位递归。当个位已被固定时，添加数字的字符串。

   * 例如当 n = 2 时（数字范围 1 - 99 ），固定十位为 0 - 9 ，按顺序依次开启递归，固定个位 0 - 9 ，终止递归并添加数字字符串。

     <img src="https://pic.leetcode-cn.com/83f4b5930ddc1d42b05c724ea2950ee7f00427b11150c86b45bd88405f8c7c87-Picture1.png" alt="Picture1.png" style="zoom: 50%;" />



```java
//输出为字符串来表示大数
class Solution {
    StringBuilder res;
    int nine = 0, count = 0, start, n;
    char[] num, loop = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'};
    public String printNumbers(int n) {
        this.n = n;
        res = new StringBuilder();
        num = new char[n];
        start = n - 1;
        dfs(0);
        res.deleteCharAt(res.length() - 1);
        return res.toString();
    }
    void dfs(int x) {
        if(x == n) {
            String s = String.valueOf(num).substring(start);
            if(!s.equals("0")) res.append(s + ",");
            if(n - start == nine) start--;
            return;
        }
        for(char i : loop) {
            if(i == '9') nine++;
            num[x] = i;
            dfs(x + 1);
        }
        nine--;
    }
}
```



```java
//本题要求：输出int类型数组
class Solution {
    int[] res;
    int nine = 0, count = 0, start, n;
    char[] num, loop = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'};
    public int[] printNumbers(int n) {
        this.n = n;
        res = new int[(int)Math.pow(10, n) - 1];
        num = new char[n];
        start = n - 1;
        dfs(0);
        return res;
    }
    
    void dfs(int x) {
        if(x == n) {
            String s = String.valueOf(num).substring(start);
            if(!s.equals("0")) res[count++] = Integer.parseInt(s);
            if(n - start == nine) start--;
            return;
        }
        for(char i : loop) {
            if(i == '9') nine++;
            num[x] = i;
            dfs(x + 1);
        }
        nine--;
    }
}
```







------

### [剑指 Offer 21. 调整数组顺序使奇数位于偶数前面](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

#### 题目

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分。

#### 示例

```
输入：nums = [1,2,3,4]
输出：[1,3,2,4] 
注：[3,1,2,4] 也是正确的答案之一。
```

#### 思路

**首尾双针法**

声明首指针even和尾指针odd

- even从左往右寻找偶数
- odd从右往左寻找奇数
- 将even找到的偶数和odd找到的奇数交换

> 技巧
>
> - x&1 位运算 等价于x%2 取余运算，即皆可用于判断数字奇偶性。



------

### [剑指 Offer 39. 数组中出现次数超过一半的数字](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

#### 题目

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

#### 示例

```
输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2
```

#### 思路

1. HashMap

2. 摩尔投票法

   众数$x$：出现次数超过数组一半的数

   票数$vote$

   - 设众数x为num[i], 则 vote+1
   - 如果num[i+1] != x, 则 vote-1
   - 如果vote==0， 则x=num[i+2]

------

### [剑指 Offer 42. 连续子数组的最大和](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

#### 题目

输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

#### 示例

```
输入: nums = [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

#### 思路

**动态规划**。

创建一个dp数组，用于保存前nums[i]的最大和。

转移方程：

- dp[i-1] > 0, dp[i] = dp[i-1] + nums[i]
- dp[i-1] < 0, dp[i] = nums[i]

最后，然后输出dp中的最大值。   



------

### [剑指 Offer 45. 把数组排成最小的数](https://leetcode-cn.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

#### 题目

输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

#### 示例

```
输入: [10,2]
输出: "102"
```

```
输入: [3,30,34,5,9]
输出: "3033459"
```

#### 思路

对于字符串x, y

- x + y > y + x, 则y在x左边
- x + y < y + x, 则x在y左边



------

### [剑指 Offer 56 - I. 数组中数字出现的次数](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

#### 题目

一个整型数组 `nums` 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

#### 示例

```
输入：nums = [4,1,4,6]
输出：[1,6] 或 [6,1]
```

```
输入：nums = [1,2,10,4,1,4,3,3]
输出：[2,10] 或 [10,2]
```

#### 思路

以[4, 1, 4, 3, 3, 6]为例，只出现一次的数字是[1, 6]

1. 遍历数组做异或运算，得到结果为 1^6 = 7
2. 循环左移数字1，和7做与运算，找到1^6从右往左的第一个不一样的位数
3. 根据这一个不一样的位数来把数组里的数分成两个子数组，这样一个数组包含了1，一个数组包含了6，而相同的数字也会被包含到一个数组里。
4. 两个子数组分别做异或运算，分别得到1和6，并输出。



------

### [剑指 Offer 56 - II. 数组中数字出现的次数 II](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

#### 题目

在一个数组 `nums` 中除一个数字只出现一次之外，其他数字都出现了**三**次。请找出那个只出现一次的数字。

#### 示例

```
输入：nums = [3,4,3,3]
输出：4
```

```
输入：nums = [9,1,7,9,7,9,7]
输出：1
```

#### 思路

考虑二进制。对于出现三次的数字的位数的1的数量一定是3的倍数。所以统计二进制位1的个数，并对3求余，结果就是只出现1次的数字。

<img src="https://pic.leetcode-cn.com/28f2379be5beccb877c8f1586d8673a256594e0fc45422b03773b8d4c8418825-Picture1.png" alt="Picture1.png" style="zoom: 50%;" />

用**有限状态机**来完成统计。

- 建立状态图：用于统计1的个数。以最低位为例，如果第一个数字的最低为是1（01），下一个数字的最低位是1（01），则状态进入10，表示现在有两个1；再下一个数字的最低位还是1，则状态进入00。

  <img src="https://pic.leetcode-cn.com/ab00d4d1ad961a3cd4fc1840e34866992571162096000325e7ce10ff75fda770-Picture2.png" alt="Picture2.png" style="zoom:50%;" />

  <img src="https://pic.leetcode-cn.com/0a7ea5bca055b095673620d8bb4c98ef6c610a22f999294ed11ae35d43621e93-Picture3.png" alt="Picture3.png" style="zoom:50%;" />

- 建立状态转换表

  - 计算one

  <img src="https://pic.leetcode-cn.com/f75d89219ad93c69757b187c64784b4c7a57dce7911884fe82f14073d654d32f-Picture4.png" alt="Picture4.png" style="zoom:50%;" />

  - 计算two

    <img src="https://pic.leetcode-cn.com/6ba76dba1ac98ee2bb982e011fdffd1df9a6963f157b2780461dbce453f0ded3-Picture5.png" alt="Picture5.png" style="zoom:50%;" />



------

### [剑指 Offer 57. 和为s的两个数字](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

#### 题目

输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

#### 示例

```
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
```

```
输入：nums = [10,26,30,31,47,60], target = 40
输出：[10,30] 或者 [30,10]
```

#### 思路

双指针对撞。

- nums[i] + nums[j] < target，则i++;
- nums[i] + nums[j] > target，则j--;



------

### [剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

#### 题目

输入一个正整数 `target` ，输出所有和为 `target` 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列

#### 示例

```
输入：target = 9
输出：[[2,3,4],[4,5]]
```

```
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

#### 思路

**方法一**

求和公式

![image-20211223114926256](https://gitee.com/FinnSHI/PicBed/raw/master/imgs/202112231149399.png)

**方法二** 

滑动窗口

<br/>

<br/>

# 链表

## [剑指 Offer 06. 从尾头打印链表](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

### 题目

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

### 示例

```
输入：head = [1,3,2]
输出：[2,3,1]
```

### 思路

1. 可以用栈来实现——鲁棒性高，但是需要额外的空间。
2. 可以用递归来实现（递归本身就是一个栈）——链表太长的时候，可能会导致函数调用用栈溢出。 

### 错误分析

```java
class Solution {
    public int[] reversePrint(ListNode head) {
        Stack<Integer> stack = new Stack<Integer>();
        ListNode p = head;
        while(p != null) {
            stack.push(p.val);
            p = p.next;
        }
        int[] res = new int[stack.size()];
        for(int i=0; i<stack.size(); i++) {
                res[i] = stack.pop();
        }
        return res;
    }
}

/*
结果：最后一个值总是打印不出来。比如输入1,3,2； 返回的是2，3，0
原因：随着stack.pop(), stack.size()会变化。 
*/
```



------

## [剑指 Offer 18. 删除链表的节点](https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

### 题目

给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。返回删除后的链表的头节点。

### 示例

```
输入: head = [4,5,1,9], val = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9
```

```
输入: head = [4,5,1,9], val = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.
```

### 思路

单指针。看下一个Node的`val`是否等于指定的`val`。

```java
class Solution {
    public ListNode deleteNode(ListNode head, int val) {
        //如果链表为空
        if(head == null)
            return head;
        //如果链表第一个节点就是val
        if(head.val == val) {
            head = head.next;
            return head;
        }   
        ListNode cur = head;
        while((cur != null) && (cur.next != null)){
            if(cur.next.val == val){
                cur.next = cur.next.next;
            }
            cur = cur.next;
        }
        return head;
    }
}
```

### 注意

第12行，进行判断条件` while((cur != null) && (cur.next != null))`的时候，要先把`cur!=null`放在前面，因为当`cur`是null的时候，如果先判断`cur.next`的时候会空指针异常。

------

## [剑指 Offer 22. 链表中倒数第k个节点](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

### 题目

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。

### 示例

```
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5
```

### 思路

使用快慢指针，快指针先走k个，然后快慢指针一起走，直到快指针到头。

- 快慢指针p，q：
  - p先走k个链表，然后p和q一起走，直到p走到头
  - 返回q



------

## [剑指 Offer 24. 反转链表](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

### 题目

定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

### 示例

```
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

### 思路

三个节点，前中后。



------

## [剑指 Offer 25. 合并两个排序的链表](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

### 题目

输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

### 示例

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

### 思路

递归。



------

## [剑指 Offer 52. 两个链表的第一个公共节点](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

### 题目

输入两个链表，找出它们的第一个公共节点。

### 示例

![img](https://raw.githubusercontent.com/FinnSHI/PictureBed/main/imgs/202110261138958.png)

```
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，两个列表的相交节点不能为0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
```

![img](https://raw.githubusercontent.com/FinnSHI/PictureBed/main/imgs/202110261138328.png)

```
输入：intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
输出：null
输入解释：从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
解释：这两个链表不相交，因此返回 null。
```

### 思路

#### 方法一 哈希集合

1. 遍历一遍链表A，把链表A中每个值都加入哈希集合。
2. 遍历链表B：
   - 直到找到第一个在哈希集合中的节点；
   - 若找不到，则返回null。

**时间复杂度**：$O(m+n)$

**空间复杂度**：$O(m)$





#### 方法二 双指针

1. 链表相交：A和B都同时跑自己的和对方的链表，直到相交
   - A跑完自己的，就去跑B的
   - B跑完自己的，就去跑A的

2. 链表不相交，A和B跑到链表尾变成null后结束

```java
/* 双指针 */ 
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if((headA == null) || (headB == null))
            return null;
        ListNode p = headA;
        ListNode q = headB;
        while(p != q){
            p = (p == null) ? headB: p.next;
            q = (q == null) ? headA: q.next;
        }
        return p;
    }
}
```

**时间复杂度**：$O(m+n)$

**空间复杂度**：$O(1)$



<br/>

<br/>

# 栈

## [剑指 Offer 09. 用两个栈实现队列](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

### 题目

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )。

### 示例

```
输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]
```



```
输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
```

### 思路

用两个栈来模拟队列：

* stack1用于队尾插入操作。添加的数据放入stack1中。

* stack2用于队头删除操作。要删除队尾元素，

  * stack2为空时

    a) stack1不为空，只需将stack1中所有数据弹入stack2，然后pop栈顶元素

    b) stack1为空，说明两个栈都没元素，return -1；

  * stack2不为空，直接弹出栈顶元素。

    

------

## [剑指 Offer 30. 包含min函数的栈](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

### 题目

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度**都是 O(1)**。

### 示例

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.
```

### 思路

主栈A， 实现push, pop, top的功能

辅助栈B，实现min功能

注意：

Stack中保存的是Integer对象，因此比较元素时，不能用==，而是用equals()

<br/>

<br/>

# 队列





# 二叉树

## [剑指 Offer 07. 重建二叉树(⭐)](https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof/)

### 题目

输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

### 示例

```
1:
Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]

2:
Input: preorder = [-1], inorder = [-1]
Output: [-1]
```

### 思路

1. 递归: 每层递归中，preorder的第一个元素就是根节点，在inorder中找到该节点的位置，则左树是该节点左边的元素，右树是节点右边的元素，注意数组的边界。

2. 迭代


------

## [剑指 Offer 26. 树的子结构](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)

### 题目

输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。

![image-20211207164340801](https://gitee.com/FinnSHI/PicBed/raw/master/imgs/202112071643977.png)

返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。

### 示例

```
输入：A = [1,2,3], B = [3,1]
输出：false

输入：A = [3,4,5,1,2], B = [4,1]
输出：true
```

### 思路

**先序遍历A树**

先在A中找到B的根节点：





------

## [剑指 Offer 27. 二叉树的镜像](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

### 题目

请完成一个函数，输入一个二叉树，该函数输出它的镜像。

<img src="https://raw.githubusercontent.com/FinnSHI/PictureBed/main/imgs/202110282301251.png" alt="image-20211028230110185" style="zoom: 67%;" />

### 示例

```
输入：root = [4,2,7,1,3,6,9]
输出：[4,7,2,9,6,3,1]
```

### 思路

后序遍历递归root的左、右子树



------

## [剑指 Offer 28. 对称的二叉树](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

### 题目

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

​	1

   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

​	1

   / \
  2   2
   \   \
   3    3

### 示例

```
输入：root = [1,2,2,3,4,4,3]
输出：true

输入：root = [1,2,2,null,3,null,3]
输出：false
```

### 思路

递归

如果L和R是两个对称的节点，则比较

- L.left 和 R.right
- L.right 和 R.left

终止条件：L或R为null

------

## [剑指 Offer 32 - I. 从上到下打印二叉树](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

### 题目

从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

### 示例

给定二叉树: [3,9,20,null,null,15,7],

        3
       / \
      9  20
        /  \
       15   7
       
    返回：[3,9,20,15,7]

### 注意

ArrayList是动态数组，其size()方法，会随着数组remove()的发生而变化



------

## [剑指 Offer 32 - II. 从上到下打印二叉树 II（java队列）](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

### 题目

从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

### 示例

```
例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7


返回其层次遍历结果：

[
  [3],
  [9,20],
  [15,7]
]
```

### 思路

用队列

1. 用Queue来实现层次遍历。Java中Queue接口由LinkedList实现。

   ```java
   Queue<TreeNode> queue = new LinkedList<>();
   ```

![](https://raw.githubusercontent.com/FinnSHI/PictureBed/main/imgs/202111081049958.png)

2. 动态二维数组来输出结果。

   ```java
   List<List<Integer>> res = new ArrayList<>();
   ```




------

## [剑指 Offer 32 - III. 从上到下打印二叉树 III](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

### 题目

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

### 示例

给定二叉树: `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```
[
  [3],
  [20,9],
  [15,7]
]
```

### 思路

奇偶层逻辑分离



## [剑指 Offer 33. 二叉搜索树的后序遍历序列](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

### 题目

输入一个整数数组，判断该数组是不是某**二叉搜索树**的后序遍历结果。如果是则返回 `true`，否则返回 `false`。假设输入的数组的任意两个数字都互不相同。

### 示例

         5
        / \
       2   6
      / \
     1   3
     
    输入: [1,6,3,2,5]
    输出: false
    
    输入: [1,3,2,6,5]
    输出: true
### 思路

1.先得到树的后序遍历，再和数组进行比较。

2.

二叉搜索树性质：





------

## [剑指 Offer 54. 二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

### 题目

给定一棵二叉搜索树，请找出其中第k大的节点。

### 示例

```
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4

输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 4
```

### 性质

二叉搜索树的中序遍历为 **递增序列**

### 思路

可以找二叉搜索树中序遍历的**倒序**。就是右-根-左。



------

## [剑指 Offer 55 - I. 二叉树的深度](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)

### 题目

输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

例如：

给定二叉树 [3,9,20,null,null,15,7]，

### 示例

```
    3
   / \
  9  20
    /  \
   15   7
```

返回它的最大深度 3 。

### 思路

1. 层次遍历（BFS）
2. 递归

------

## [剑指 Offer 55 - II. 平衡二叉树](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

### 题目

输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。

### 示例

```
    3
   / \
  9  20
    /  \
   15   7
```

返回true。

```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```

返回false。

### 思路

1. 自底而上

   后序遍历+剪纸

   - 对于节点node，如果左右子树深度差$<=1$，
     - 则返回其左右子树的最大深度 = $max(left, right) + 1$
   - 如果左右子树深度差$>1$，
     - 则返回-1

2. 自上而下

   先序遍历+判断深度

------

## [剑指 Offer 68 - I. 二叉搜索树的最近公共祖先](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-zui-jin-gong-gong-zu-xian-lcof/)

### 题目

给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为：“对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（一个节点也可以是它自己的祖先）。”

### 示例

例如，给定如下二叉搜索树:  root = [6,2,8,0,4,7,9,null,null,3,5]

![img](https://gitee.com/FinnSHI/PicBed/raw/master/imgs/202112051048149.png)

```
示例 1:
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
输出: 6 
解释: 节点 2 和节点 8 的最近公共祖先是 6。

示例 2:
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
输出: 2
解释: 节点 2 和节点 4 的最近公共祖先是 2, 因为根据定义最近公共祖先节点可以为节点本身。
```

### 思路

**方法一**

p,q分别遍历，且打印路径

- 因为是二叉搜索树，很容易找到p和q的路径，分别用list保存，然后遍历两条path，找到最近公共祖先节点

**方法二**

p和q一起遍历，设当前节点是ancestor

- ancestor < p,q，pq在ancestor右子树，则ancestor向right移动
- ancestor > p,q，pq在ancestor左子树，则ancestor向left移动
- 否则，ancestor是公共节点，或ancestor=p or q

### 复杂度

**方法二**

时间复杂度：$O(n)$

空间复杂度：$O(1)$

------

## [剑指 Offer 68 - II. 二叉树的最近公共祖先](https://leetcode-cn.com/problems/er-cha-shu-de-zui-jin-gong-gong-zu-xian-lcof/)

### 题目

给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

例如，给定如下二叉树:  root = [3,5,1,6,2,0,8,null,null,7,4]

![img](https://gitee.com/FinnSHI/PicBed/raw/master/imgs/202112051115153.png)

### 示例

```
示例 1:
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
输出: 3
解释: 节点 5 和节点 1 的最近公共祖先是节点 3。

示例 2:
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
输出: 5
解释: 节点 5 和节点 4 的最近公共祖先是节点 5。因为根据定义最近公共祖先节点可以为节点本身。
```

### 思路

**先序遍历**。设p和q的最近公共祖先为node，有三种情况：

1. p和q在node的左、右子树中
2. p=node
3. q=node

递归解析：

- 终止条件：
  当越过叶节点，则直接返回 null ；
  当 node 等于 p, q，则直接返回 node；
- 递推工作：
  开启递归左子节点，返回值记为 left ；
  开启递归右子节点，返回值记为 right；
- 返回值： 根据 left 和 right ，对于某一个node节点，可展开为四种情况；
  - 当 left 和 right 都是null，返回 null；
  - 当 left 和 right 同时不为null ：说明 p, q 分列在 node 的左、右子树，因此 node 为最近公共祖先，返回node；
  - 当 left 为空 ，right 不为空，返回 right 。
  - 当 left 不为空 ， right 为空 ，返回left；

<br/>

<br/>

# 图

## [剑指 Offer 12. 矩阵中的路径(⭐DFS)](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/)

### 题目

给定一个 $m x n$ 二维字符网格 $board$ 和一个字符串单词 $word$ 。如果 $word$ 存在于网格中，返回 $true$ ；否则，返回 $false$ 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

例如，在下面的 3×4 的矩阵中包含单词 "ABCCED"（单词中的字母已标出）。

![img](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg)



### 示例

```
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
```

```
输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false
```

### 思路: DFS+剪枝

**典型的矩阵搜索问题**







<br/>

<br/>

# 查找

> (left + right) / 2 可以用left + ((rigth - left) >> 1))代替



## [剑指 Offer 11. 旋转数组的最小数字(二分查找)](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)

### 题目

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

### 示例

```
输入：[3,4,5,1,2]
输出：1
```

```
输入：[2,2,2,0,1]
输出：0
```

### 思路：二分查找

<img src="https://assets.leetcode-cn.com/solution-static/jianzhi_11/1.png" alt="fig1" style="zoom:33%;" />

设数组中最小值为$x$， 最后一个元素为$n$，则

* $x$左边的元素都大于$n$
* $x$右边的元素都小于$n$

所以用二分查找。



**二分查找：**

设置三个变量： left，pivot，right

​	终止条件：$left == right$

1. 当$numbers[pivot] < numbers[right]$时：最小值在$pivot$的左边。忽略$pivot$右半区间。$right = pivot$

   <img src="https://assets.leetcode-cn.com/solution-static/jianzhi_11/2.png" alt="fig2" style="zoom: 33%;" />

2. 当$numbers[pivot] > numbers[right]$时：最小值在$pivot$的右边。忽略$pivot$左半区间。$left = pivot + 1$，要+1，否则$left$和$right$相邻的时候，就死循环了。

   <img src="https://assets.leetcode-cn.com/solution-static/jianzhi_11/3.png" alt="fig3" style="zoom:33%;" />

3. 当$numbers[pivot] == numbers[right]$时：最小值可能在$pivot$左边，也可能在$pivot$的右边。可以将右端点向前移一格（因为我们这题是通过比较$pivot$和$right$节点的值来找最小值的）。

<img src="https://assets.leetcode-cn.com/solution-static/jianzhi_11/4.png" alt="fig4" style="zoom:33%;" />

**时间复杂度：$O(n)$**

**空间复杂度：$O(1)$**



### 注意

在求$pivot = (left + right)/2$的时候，为了防止$left+right$发生越界，所以用$pivot = (right - left)/2 + left$来求。

**解：**

$pivot=(left+right)/2=left/2+right/2=right/2-left/2+left=(right-left)/2+left$





## [剑指 Offer 53 - I. 在排序数组中查找数字 I](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

### 题目

统计一个数字在排序数组中出现的次数。

### 示例

```
输入: nums = [5,7,7,8,8,10], target = 8
输出: 2
```

```
输入: nums = [5,7,7,8,8,10], target = 6
输出: 0
```

### 思路

二分查找：

用两次二分查找法找到相同数字的左右边界，然后根据左右边界求出答案。



------

## [剑指 Offer 53 - II. 0～n-1中缺失的数字](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

### 题目

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

### 示例

```
输入: [0,1,3]
输出: 2
```

```
输入: [0,1,2,3,4,5,6,7,9]
输出: 8
```

### 思路

排序数组中寻找数字，首先想到**二分法**。

用二分法来找右数组的首元素。比如：[9]就是[0,1,2,3,4,5,6,7,9]的右数组，[0,1,2,3,4,5,6,7]是[0,1,2,3,4,5,6,7,9]的左数组



------

### 



<br/>

<br/>

# 排序









# 动态规划

## [剑指 Offer 10. 斐波那契数列⭐](https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/)

### 题目

写一个函数，输入 `n` ，求斐波那契（Fibonacci）数列的第 `n` 项（即 `F(N)`）。斐波那契数列的定义如下：

$F(0) = 0,   F(1) = 1, 
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.$

斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 $1e9+7$（1000000007），如计算初始结果为：1000000008，请返回 1。

### 示例

```
输入：n = 2
输出：1
```

```
输入：n = 5
输出：5
```

### 错误分析

用递归实现

时间复杂度：$O(2^n)$

空间复杂度：$O(n)$

```java
class Solution {
    public int fib(int n) {
        if(n == 0 )
            return 0;
        else if(n == 1)
            return 1;
        return (fib(n-1) + fib(n-2));
    }
}
```

时间超时。

因为会进行大量重复的运算，时间复杂度太高了。

<img src="https://pic.leetcode-cn.com/25e913ab8d7a22bb017669e4a097cf51d10861f365002f2d8556ee7a64464cd8-Picture0.png" alt="Picture0.png" style="zoom:50%;" />

### 解题

#### 方法一：动态规划

##### 动态规划：

用于解决最优方法

* 状态定义： 设 $dp$为一维数组，其中 $dp[i]$ 的值代表 斐波那契数列第 $i$ 个数字 。
* 转移方程： $dp[i + 1] = dp[i] + dp[i - 1], dp[i+1]=dp[i]+dp[i−1]$ ，即对应数列定义 $f(n + 1) = f(n) + f(n - 1), f(n+1)=f(n)+f(n−1)$ ；
* 初始状态： $dp[0] = 0, dp[1] = 1$，即初始化前两个数字；
* 返回值： $dp[n]$ ，即斐波那契数列的第 $n$ 个数字。

##### 解题：

时间复杂度：$O(n)$

空间复杂度：$O(1)$

由于斐波那契数存在**<font color="red">递推</font>**关系，因此可以使用**<font color="red">动态规划</font>**求解。动态规划的状态转移方程即为上述递推关系，边界条件为 $F(0)$ 和 $F(1)$。

1. 先用穷举法
2. 再考虑用数组保存计算过的$F(n)$的值
3. 优化：

* 可以使用「滚动数组思想」把空间复杂度优化成 $O(1)$。

* 滚动数组长度为3，用来保存$F(N) ,F(N - 1),F(N - 2)$

#### 方法二：矩阵快速幂

![image-20210924161147712](E:\Typora_Documents\Data Structure\imgs\数据结构.assets\image-20210924161147712.png)



------

## [剑指 Offer 10. 青蛙跳台阶问题](https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)

### 题目

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

### 示例

```
输入：n = 2
输出：2
```

```
输入：n = 7
输出：21
```

```
输入：n = 0
输出：1
```

### 思路

本质上还是斐波那契数列 $f(n+1) = f(n) + f(n-1)$：

* 蛙蛙跳上第1级台阶，还剩 n-1 级台阶，有$f(n-1)$ 种跳法
* 蛙蛙跳上第2级台阶，还剩 n-2 级台阶，有$f(n-2)$ 种跳法
* ...
* 蛙蛙跳上第n-1级台阶，还剩 1 级台阶， $f(1)$ 种跳法
* 蛙蛙跳上第n级台阶，还剩 0 级台阶， $f(0)$ 种跳法

 $f(0)=1,f(1)=1 => f(2)=2$ 



<br/>

<br/>
