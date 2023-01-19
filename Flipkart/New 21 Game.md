(Leetcode Problem) 
Alice plays the following game, loosely based on the card game "21".

Alice starts with 0 points and draws numbers while she has less than k points. During each draw, she gains an integer number of points randomly from the range [1, maxPts], where maxPts is an integer. Each draw is independent and the outcomes have equal probabilities.

Alice stops drawing numbers when she gets k or more points.

Return the probability that Alice has n or fewer points.

Answers within 10-5 of the actual answer are considered accepted.

 

Example 1:

Input: n = 10, k = 1, maxPts = 10
Output: 1.00000
Explanation: Alice gets a single card, then stops.



CODE (JAVA) :

```
class Solution {


    public double new21Game(int n, int k, int maxPts) {
        if (k == 0 || n >= k + maxPts) return 1;
        double dp[] = new double[n + 1],  maxPtssum = 1, res = 0;
        dp[0] = 1;
        for (int i = 1; i <= n; ++i) {
            dp[i] = maxPtssum / maxPts;
            if (i < k) maxPtssum += dp[i]; else res += dp[i];
            if (i - maxPts >= 0) maxPtssum -= dp[i - maxPts];
        }
        return res;
    // public double new21Game(int n, int k, int maxPts) {
    //             if (k == 0) {
    //         return 1;
    //     }
    //     int max = k + maxPts - 1;
    //     double[] dp = new double[max + 1];
    //     dp[0] = 1;
    //     for (int i = 1; i <= max; i++) {
    //         for (int j = 1; j <= maxPts; j++) {
    //             if (i - j >= 0 && i - j < k) {
    //                 dp[i] += dp[i - j] / maxPts;
    //             }
    //         }
    //     }
    //     double result = 0;
    //     for (int i = k; i <= n; i++) {
    //         result += dp[i];
    //     }
    //     return result;
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-20 004953](https://user-images.githubusercontent.com/73281015/213539731-8c6d782f-4bf5-4522-84f1-6c9a84aedec2.png)

