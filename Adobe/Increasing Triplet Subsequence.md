(Leetcode Problem) 

Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.

 

Example 1:

Input: nums = [1,2,3,4,5]
Output: true
Explanation: Any triplet where i < j < k is valid.


CODE (JAVA) :

```
class Solution {
    public boolean increasingTriplet(int[] nums) {
 int l=Integer.MAX_VALUE;
  int m=Integer.MAX_VALUE;
  for(var x:nums){
      if(x>m) return true;
     else if(x>l && x<m) m=x;
      else if(x<l) l=x;
  }
  return false;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-11 194225](https://user-images.githubusercontent.com/73281015/211827993-e157816a-582d-4bd9-996c-7b3e4343c9a6.png)
