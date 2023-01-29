

(Leetcode Problem) 
There are n cities connected by some number of flights. You are given an array flights where flights[i] = [fromi, toi, pricei] indicates that there is a flight from city fromi to city toi with cost pricei.

You are also given three integers src, dst, and k, return the cheapest price from src to dst with at most k stops. If there is no such route, return -1.

 

Example 1:


Input: n = 4, flights = [[0,1,100],[1,2,100],[2,0,100],[1,3,600],[2,3,200]], src = 0, dst = 3, k = 1
Output: 700
Explanation:
The graph is shown above.
The optimal path with at most 1 stop from city 0 to 3 is marked in red and has cost 100 + 600 = 700.
Note that the path through cities [0,1,2,3] is cheaper but is invalid because it uses 2 stops.



CODE (JAVA) :

```
class Solution {
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int K) {
        int[][] graph = new int[n][n];
        for (int[] flight : flights) {
            int u = flight[0], v = flight[1], c = flight[2];
            graph[u][v] = c;
        }

        int[] cost = new int[n];
        Arrays.fill(cost, -1);
        Queue<Integer> queue = new ArrayDeque<>();
        queue.offer(src);
        cost[src] = 0;

        while (K >= 0) {
            int[] newCost = Arrays.copyOf(cost, cost.length);
            for (int qLen = queue.size(); qLen > 0; qLen--) {
                int from = queue.poll();
                int initCost = cost[from];
                
                for(int next = 0; next < n; next++) {
                    if (graph[from][next] == 0) continue;
                    if (newCost[next] == -1 || graph[from][next] + initCost < newCost[next]) {
                        queue.offer(next);
                        newCost[next] = graph[from][next] + initCost;
                    }
                }
            }
            cost = newCost;
            K--;
        }
        return cost[dst];
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-29 234916](https://user-images.githubusercontent.com/73281015/215347512-4fd0ab90-4ff0-41c5-89f6-cebf5f0ad07a.png)

