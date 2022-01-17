Find All Numbers Disappeared in an Array (Easy)
题目描述
给你一个含 n 个整数的数组 nums ，其中 nums[i] 在区间 [1, n] 内。请你找出所有在 [1, n] 范围内但没有出现在 nums 中的数字，并以数组的形式返回结果。

输入输出样例
输入是一个一维整数数组，输出也是一个一维整数数组，表示输入数组内没出现过的数字。
Input: [4,3,2,7,8,2,3,1]
Output: [5,6]

解：（原地哈希）
遍历两次数组。
第一次遍历：指针遍历，把数组里的数放到对应的位置上去，比如指针指向的第一个数是4，4应该出现在数组的第四个位置（nums[3]），所以4和7交换。如果指针所在的位置和所指数应该在的位置相等，就让指针加一。
第二次遍历：把对应位置应该出现但未出现的数return。
时间复杂度：O(n)
空间复杂度：O(1)

代码：
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int tem = 0;
        int index = 0, targetIndex = 0;
        while(index < nums.length) {
            if(nums[index] == index + 1) {
                index++;
            } else {
                targetIndex = nums[index] - 1;
                if(nums[index] == nums[targetIndex]){
                    index++;
                    continue;
                }
                tem = nums[index];
                nums[index] = nums[tem-1];
                nums[tem-1] = tem;
            }
        }

        List<Integer> ans = new ArrayList<>();
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] != i+1) 
                ans.add(i+1);
        }

        return ans;
    }
}