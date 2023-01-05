(Leetcode Problem)

Given a set of distinct positive integers nums, return the largest subset answer such that every pair (answer[i], answer[j]) of elements in this subset satisfies:

answer[i] % answer[j] == 0, or
answer[j] % answer[i] == 0
If there are multiple solutions, return any of them.

Example 1
Input: nums = [1,2,3]
Output: [1,2]
Explanation: [1,3] is also accepted.

CODE (JAVA) :

```
class Solution {
    public List<Integer> largestDivisibleSubset(int[] nums) {
        LinkedList<Integer> res = new LinkedList<>();
        if(nums.length == 0) return res;
        
        Arrays.sort(nums);
        int[] dp = new int[nums.length];
        int[] parent = new int[nums.length];
        int maxPos = 0;
        parent[0] = -1;
        
        for(int i=1; i<nums.length; i++){
            parent[i] = -1;
            for(int j=i-1; j>=0; j--){
                if(nums[i] % nums[j] == 0 && dp[i] < (1+dp[j]) ){
                    dp[i] = 1 + dp[j];
                    parent[i] = j;
                }
            }

            if(dp[i] > dp[maxPos]) maxPos = i;
        }
        
        while(maxPos >= 0){
            res.addFirst(nums[maxPos]);
            maxPos = parent[maxPos];
        }
        
        return res;
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-05 ](https://user-images.githubusercontent.com/73281015/210771347-e8be8408-9995-4f18-a373-c4316ec753cb.png)
