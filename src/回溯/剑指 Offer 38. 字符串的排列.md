# [剑指 Offer 38. 字符串的排列](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

## 题目

输入一个字符串，打印出该字符串中字符的所有排列。

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

```
示例:
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
```

## 思路

**经典回溯题**

![47.全排列II1](https://pic.leetcode-cn.com/1624324811-UZLaVi-file_1624324809555)



去重代码1：

```
if (i > 0 && nums[i] == nums[i - 1] && used[i - 1] == false) {
    continue;
}
```

![47.全排列II2](https://pic.leetcode-cn.com/1624324811-fZNJkE-file_1624324809080)



去重代码2：

```
if (i > 0 && nums[i] == nums[i - 1] && used[i - 1] == true) {
    continue;
}
```

![47.全排列II3](https://pic.leetcode-cn.com/1624324811-vGuFvc-file_1624324809536)



明显去重代码1更好。



## 代码

```java
class Solution {
    List<String> resList;
    StringBuilder path;
    boolean[] used;

    public String[] permutation(String s) {
        resList = new ArrayList<>();
        path = new StringBuilder();
        used = new boolean[s.length()];

        char[] chars = s.toCharArray();
        Arrays.sort(chars);
        Arrays.fill(used, false);
        backtrack(chars, used);
        return resList.toArray(new String[0]);
    }

    public void backtrack(char[] chars, boolean[] used){
        // 找到一组合适
        if(path.length() == chars.length) {
            System.out.println(path);
            resList.add(path.toString());
            return;
        }
        // 横向遍历
        for(int i = 0; i < chars.length; i++) {
            // 同一个树层
            // 出现重复的元素
            if(i > 0 && chars[i] == chars[i-1] && used[i-1] == false)
                continue;
            if(used[i] == false) {
                used[i] = true;
                path.append(chars[i]);
                // 纵向遍历
                backtrack(chars, used);
                path.deleteCharAt(path.length() - 1); // 去掉同一层的 
                used[i] = false;
            }
        }
    }
}
```

## 复杂度

时间复杂度：$O(n × n!)$

空间复杂度：$O(n)$   

