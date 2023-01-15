

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
          int max=Integer.MIN_VALUE, min=Integer.MAX_VALUE;
        //   int len=nums.length;
        // int start=-1, end=-1;
        
        // for(int i=0; i<len; i++){
        //     max = Math.max(max, nums[i]); 
        //     min = Math.min(min, nums[len-i-1]);  
            
        //     if(nums[i] < max)  
        //         end = i;
        //     if(nums[len-i-1] > min)
        //         start = len-i-1;
        // }
        
        // if(start==-1)
        //     return 0;
        
        // return end-start+1;
for(int i=0; i<nums.length-1;i++){
    if(nums[i]>nums[i+1]) min=Math.min(min,nums[i+1]);
}
for(int i=nums.length-1; i>0;i--){
    if(nums[i-1]>nums[i]) max=Math.max(max,nums[i-1]);
}
int l=0 ,r= 0;
for(int i=0; i<nums.length;i++){
    if(nums[i]>min){
        l=i; break;
    }
}
for(int i=nums.length-1; i>=0;i--){
    if(nums[i]<max) {
        r=i; break;
    } 
}
  return r-l>0 ?r-l+1:0;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-15 090924](https://user-images.githubusercontent.com/73281015/212521801-dd5ed8d0-6946-42e8-a849-d8e02ccc68a5.png)

