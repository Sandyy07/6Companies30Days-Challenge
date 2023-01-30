(Leetcode Problem) 
You are given two positive integers startPos and endPos. Initially, you are standing at position startPos on an infinite number line. With one step, you can move either one position to the left, or one position to the right.

Given a positive integer k, return the number of different ways to reach the position endPos starting from startPos, such that you perform exactly k steps. Since the answer may be very large, return it modulo 109 + 7.

Two ways are considered different if the order of the steps made is not exactly the same.

Note that the number line includes negative integers.

 

Example 1:

Input: startPos = 1, endPos = 2, k = 3
Output: 3
Explanation: We can reach position 2 from 1 in exactly 3 steps in three ways:
- 1 -> 2 -> 3 -> 2.
- 1 -> 2 -> 1 -> 2.
- 1 -> 0 -> 1 -> 2.
It can be proven that no other way is possible, so we return 3.



CODE (JAVA) :

```
class Solution {
    public int numberOfWays(int startPos, int endPos, int k) {
        int dp[][]=new int[4001][1001];
        for(var x:dp) Arrays.fill(x,-1);
          int a=g(startPos,endPos,k,dp);
          return (int)a%1000000007;
    }

    int g(int s, int e, int k, int[][] dp){
        if(k==0 && s==e) return 1;
        if(k==0) return 0;
        if(dp[s+1000][k]!=-1) return dp[s+1000][k];
        int a=g(s+1,e,k-1,dp);
        a+=g(s-1,e,k-1,dp);
        return dp[s+1000][k]=a%1000000007;
    } 
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-30 110830](https://user-images.githubusercontent.com/73281015/215396086-2b29b43f-49cb-456f-a6cb-788e848b9a68.png)
