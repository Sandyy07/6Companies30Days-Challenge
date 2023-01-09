(Leetcode Problem)
You are given an integer array nums that is sorted in non-decreasing order.

Determine if it is possible to split nums into one or more subsequences such that both of the following conditions are true:

Each subsequence is a consecutive increasing sequence (i.e. each integer is exactly one more than the previous integer).
All subsequences have a length of 3 or more.
Return true if you can split nums according to the above conditions, or false otherwise.

A subsequence of an array is a new array that is formed from the original array by deleting some (can be none) of the elements without disturbing the relative positions of the remaining elements. (i.e., [1,3,5] is a subsequence of [1,2,3,4,5] while [1,3,2] is not).

 

Example 1:

Input: nums = [1,2,3,3,4,5]
Output: true
Explanation: nums can be split into the following subsequences:
[1,2,3,3,4,5] --> 1, 2, 3
[1,2,3,3,4,5] --> 3, 4, 5

CODE (JAVA) :

  ```
  class Solution {
    public boolean isPossible(int[] nums) {
        HashMap<Integer , Integer> am=new HashMap<>();
    HashMap<Integer , Integer> vm=new HashMap<>();
    for(int i: nums) am.put(i,am.getOrDefault(i,0)+1);
    for(int i:nums){
        if(am.get(i)<=0) continue;
        else if(vm.getOrDefault(i,0)>0){
            am.put(i,am.getOrDefault(i,0)-1);
            vm.put(i,vm.getOrDefault(i,0)-1);
            vm.put(i+1,vm.getOrDefault(i+1,0)+1);
        }
        else if(am.getOrDefault(i,0)>0 && am.getOrDefault(i+1,0)>0 && am.getOrDefault(i+2,0)>0){
            am.put(i,am.getOrDefault(i,0)-1);
            am.put(i+1,am.getOrDefault(i+1,0)-1);
            am.put(i+2,am.getOrDefault(i+2,0)-1);

            vm.put(i+3,vm.getOrDefault(i+3,0)+1);


        }
        else{
            return false;
        }
    }
    return true;
    }
}
  
  ```
LEETCODE ACCEPTED :

![Screenshot 2023-01-09 120132](https://user-images.githubusercontent.com/73281015/211257399-402b0d63-bf05-4e73-8288-f7ec77bab204.png)
