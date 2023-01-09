(Leetcode Problem)

You are given an array nums that consists of non-negative integers. Let us define rev(x) as the reverse of the non-negative integer x. For example, rev(123) = 321, and rev(120) = 21. A pair of indices (i, j) is nice if it satisfies all of the following conditions:

0 <= i < j < nums.length
nums[i] + rev(nums[j]) == nums[j] + rev(nums[i])
Return the number of nice pairs of indices. Since that number can be too large, return it modulo 109 + 7.

 

Example 1:

Input: nums = [42,11,1,97]
Output: 2
Explanation: The two pairs are:
 - (0,3) : 42 + rev(97) = 42 + 79 = 121, 97 + rev(42) = 97 + 24 = 121.
 - (1,2) : 11 + rev(1) = 11 + 1 = 12, 1 + rev(11) = 1 + 11 = 12.

CODE (JAVA) :

```
class Solution {
    public int countNicePairs(int[] nums) {
       HashMap<Integer , Integer> m=new HashMap<>();
       int ans=0;
       for(var n : nums){
           ans = (ans+m.getOrDefault(n-r(n),0)) % 1000000007;
           m.put(n-r(n),m.getOrDefault(n-r(n),0) + 1);
       } 
       return ans;
    }

int r(int n) {
    int res = 0;
    for (; n > 0; n /= 10)
        res = res * 10 + n % 10;
    return res;
}   
}
```
LEETCODE ACCEPTED :

![Screenshot 2023-01-09 234203](https://user-images.githubusercontent.com/73281015/211378057-42cd9797-67a7-4e52-95a0-b35b01ef8ee4.png)
