

(Leetcode Problem) 
Given an integer array nums and an integer k, return true if it is possible to divide this array into k non-empty subsets whose sums are all equal.

 

Example 1:

Input: nums = [4,3,2,3,5,2,1], k = 4
Output: true
Explanation: It is possible to divide it into 4 subsets (5), (1, 4), (2,3), (2,3) with equal sums.



CODE (JAVA) :

```
class Solution {
    public boolean canPartitionKSubsets(int[] nums, int k) {
        int len = nums.length;
        int cursum = 0;
        for(int i: nums) cursum += i;
        if(cursum %k != 0)
            return false;
        int arr[] = new int[k];
        
        cursum /= k;
        HashMap<String, Integer> dp = new HashMap<>();
        Arrays.sort(nums);
        int newArr[] = new int[nums.length];
        for(int i = 0; i<len ; i++) {
            newArr[i] = nums[len-1-i]; 
        }
        return solve(newArr, k, 0, arr, cursum,dp);
    }
    
    public boolean solve(int nums[], int k, int curpos, int arr[], int reqSum,HashMap<String, Integer> dp) {
        
        String key = ""+curpos;
        for(int i: arr) 
            if(i != 0)
                key = key+":"+i;
        
        if(curpos == nums.length) {
            
            for(int i = 0; i< k; i++){
                if(arr[i] != reqSum){
                    dp.put(key,-1);
                    return false;
                }
            }
            dp.put(key,1);
            return true;
        }
        if(curpos >= nums.length) {
            return false;
        }
        
        
        if(dp.containsKey(key))
            return dp.get(key) == 1;
        
      for(int i = 0; i< k; i++) {
          arr[i] += nums[curpos];
          if(arr[i] <= reqSum && solve(nums, k, curpos+1, arr, reqSum, dp)){
              dp.put(key,1);
              return true;
          }
          arr[i] -= nums[curpos];
          if(arr[i] == 0){
              dp.put(key,-1);
              return false;
          }
      }  
        
        dp.put(key,-1);
        return false;
    }
}

```
LEETCODE ACCEPTED :


![Screenshot 2023-01-16 115159](https://user-images.githubusercontent.com/73281015/212611406-d43469f8-132a-441f-858d-9f5eb99bf699.png)

