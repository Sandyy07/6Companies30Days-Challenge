(Leetcode Problem)
Suppose LeetCode will start its IPO soon. In order to sell a good price of its shares to Venture Capital, LeetCode would like to work on some projects to increase its capital before the IPO. Since it has limited resources, it can only finish at most k distinct projects before the IPO. Help LeetCode design the best way to maximize its total capital after finishing at most k distinct projects.

You are given n projects where the ith project has a pure profit profits[i] and a minimum capital of capital[i] is needed to start it.

Initially, you have w capital. When you finish a project, you will obtain its pure profit and the profit will be added to your total capital.

Pick a list of at most k distinct projects from given projects to maximize your final capital, and return the final maximized capital.

The answer is guaranteed to fit in a 32-bit signed integer.

 

Example 1:

Input: k = 2, w = 0, profits = [1,2,3], capital = [0,1,1]
Output: 4
Explanation: Since your initial capital is 0, you can only start the project indexed 0.
After finishing it you will obtain profit 1 and your capital becomes 1.
With capital 1, you can either start the project indexed 1 or the project indexed 2.
Since you can choose at most 2 projects, you need to finish the project indexed 2 to get the maximum capital.
Therefore, output the final maximized capital, which is 0 + 1 + 3 = 4.

CODE (JAVA) :

```
class Solution {
  public int findMaximizedCapital(int numberOfProjects, int initialCapital, int[] profits, int[] capital) {
    int n = profits.length;
    PriorityQueue<Integer> minCapitalHeap = new PriorityQueue<>(n, (i1, i2) -> capital[i1] - capital[i2]);
    PriorityQueue<Integer> maxProfitHeap = new PriorityQueue<>(n, (i1, i2) -> profits[i2] - profits[i1]);

    for (int i = 0; i < n; i++)
      minCapitalHeap.offer(i);

    int availableCapital = initialCapital;
    for (int i = 0; i < numberOfProjects; i++) {
      while (!minCapitalHeap.isEmpty() && capital[minCapitalHeap.peek()] <= availableCapital)
        maxProfitHeap.add(minCapitalHeap.poll());

      if (maxProfitHeap.isEmpty())
        break;

      availableCapital += profits[maxProfitHeap.poll()];
    }

    return availableCapital;
  }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-10 122634](https://user-images.githubusercontent.com/73281015/211482531-6a3d50b7-0510-4633-ab05-e75139340f09.png)
