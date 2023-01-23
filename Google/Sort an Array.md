(Leetcode Problem) 

Given an array of integers nums, sort the array in ascending order and return it.

You must solve the problem without using any built-in functions in O(nlog(n)) time complexity and with the smallest space complexity possible.

 

Example 1:

Input: nums = [5,2,3,1]
Output: [1,2,3,5]
Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).


CODE (JAVA) :

```
class Solution {
    public int[] sortArray(int[] nums) {
        int max=Integer.MIN_VALUE,min=Integer.MAX_VALUE;
        for(int v:nums){
            max=Math.max(max,v);
            min=Math.min(min,v);
        }
        int len=max-min+1;
        int[] farr=new int[len]; 
        for(int i=0;i<nums.length;i++){
            int idx=nums[i]-min;
            farr[idx]++;
        }
       
         for(int i=1;i<farr.length;i++){ 
           farr[i]=farr[i-1]+farr[i];
        }
      
        int[] ans=new int[nums.length];
        for(int i=nums.length-1;i>=0;i--){
             int idx=nums[i];
            int v=farr[idx-min];
            ans[v-1]=idx;
            farr[idx-min]--;
        }
      
      
        return ans;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-23 201500](https://user-images.githubusercontent.com/73281015/214068473-cee8a386-c804-431c-ae4e-6353a2e55a41.png)

