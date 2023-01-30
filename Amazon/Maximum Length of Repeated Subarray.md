(Leetcode Problem) 
Given two integer arrays nums1 and nums2, return the maximum length of a subarray that appears in both arrays.

 

Example 1:

Input: nums1 = [1,2,3,2,1], nums2 = [3,2,1,4,7]
Output: 3
Explanation: The repeated subarray with maximum length is [3,2,1].



CODE (JAVA) :

```
class Solution {
    public int findLength(int[] A, int[] B) {
        int m = A.length, n = B.length, result = 0;
        int dp[][] = new int[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                if (i == 0 || j == 0)
                    dp[i][j] = 0;
                else if (A[i - 1] == B[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                    result = Integer.max(result, dp[i][j]);
                }
                else
                    dp[i][j] = 0;
            }
        }
        return result;
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-30 111718](https://user-images.githubusercontent.com/73281015/215397143-bfd610d5-d326-4380-80fa-d68da2d7437f.png)
