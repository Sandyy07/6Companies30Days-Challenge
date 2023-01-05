(Leetcode Problem)
Given an integer array nums, you need to find one continuous subarray that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order.

Return the shortest such subarray and output its length.

 

Example 1:

Input: nums = [2,6,4,8,10,9,15]
Output: 5
Explanation: You need to sort [6, 4, 8, 10, 9] in ascending order to make the whole array sorted in ascending order.


CODE (JAVA) :
```
  class Solution {
    public int findUnsortedSubarray(int[] nums) {
          int len=nums.length;
        int max=Integer.MIN_VALUE, min=Integer.MAX_VALUE;
        int start=-1, end=-1;
        
        for(int i=0; i<len; i++){
            max = Math.max(max, nums[i]); 
            min = Math.min(min, nums[len-i-1]);  
            
            if(nums[i] < max)  
                end = i;
            if(nums[len-i-1] > min)
                start = len-i-1;
        }
        
        if(start==-1)
            return 0;
        
        return end-start+1;
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-03 ](https://user-images.githubusercontent.com/73281015/210767847-27922e5b-c409-4fe0-a79c-517bef38bb89.png)
