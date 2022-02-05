# [剑指 Offer 49. 丑数](https://leetcode-cn.com/problems/chou-shu-lcof/)

## 题目

我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

 

```
示例:
输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
```

## 思路

**动态规划**

1. 丑数只包含质因子 2、3 和 5 ，因此丑数 = 某小丑数 × 某因子

2. 因此，得到转移方程为：

   $x[n+1] = min(x[a]*2, x[b]*3, x[c]*5)$

动态规划：

- 状态定义：丑数 = 某小丑数 × 某因子
- 转移方程：$x[n+1] = min(x[a]*2, x[b]*3, x[c]*5)$
  - $if(x[a] * 2 == x[i]) a++;$
  - $if(x[b] * 3 == x[i]) b++;$
  - $if(x[c] * 5 == x[i]) c++;$
- 初始状态：$x[0]=1,a=0,b=0,c=0$
- 返回值：$x[n-1]$

## 代码

```java
class Solution {
    public int nthUglyNumber(int n) {
        int a = 0, b = 0, c = 0;
        int[] x = new int[n];
        x[0] = 1;
        for(int i = 1; i <= n-1; i++) {
            x[i] = this.getMin(x[a] * 2, x[b] * 3, x[c] * 5);
            if(x[a] * 2 == x[i]) a++;
            if(x[b] * 3 == x[i]) b++;
            if(x[c] * 5 == x[i]) c++;
        }

        return x[n-1];
    }

    public int getMin(int a, int b, int c) {
        int minNum = Math.min(a, b);
        return Math.min(minNum, c);
    }
}
```

## 复杂度

时间复杂度：$O(N)$

空间复杂度：$O(N)$   

