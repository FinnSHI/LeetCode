# [剑指 Offer 66. 构建乘积数组](https://leetcode-cn.com/problems/gou-jian-cheng-ji-shu-zu-lcof/)

## 题目

给定一个数组 A[0,1,…,n-1]，请构建一个数组 B[0,1,…,n-1]，其中 B[i] 的值是数组 A 中除了下标 i 以外的元素的积, 即 B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]。不能使用除法。

 

```
示例:

输入: [1,2,3,4,5]
输出: [120,60,40,30,24]
```

## 思路

动态规划

- 维护两个动态规划数组pre, post
  - pre 记录 a 数组从头往后的乘积
  - post记录 a 数组从后往头的乘积



## 代码

```java
class Solution {
    public int[] constructArr(int[] a) {
        // B[i] 的值是数组 A 中除了下标 i 以外的元素的积
        int n = a.length;
        if(n == 0) return new int[0];
        int[] b = new int[n];
        b[0] = 1;
        for(int i=1; i<n; i++) {
            b[i] = b[i-1] * a[i-1];
        }

        int tem = 1;
        for(int i=n-2; i>=0; i--) {
            tem = tem * a[i+1];
            b[i] = b[i] * tem;
        }

        return b;
    }
}
```



## 复杂度

时间复杂度：$O(n)$

空间复杂度：$O(1)$ （数组 bb* 作为返回值，不计入复杂度考虑）

