(Leetcode Problem) 
You are given a network of n nodes, labeled from 1 to n. You are also given times, a list of travel times as directed edges times[i] = (ui, vi, wi), where ui is the source node, vi is the target node, and wi is the time it takes for a signal to travel from source to target.

We will send a signal from a given node k. Return the minimum time it takes for all the n nodes to receive the signal. If it is impossible for all the n nodes to receive the signal, return -1.

 

Example 1:


Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
Output: 2



CODE (JAVA) :

```
class Solution {
    public int networkDelayTime(int[][] times, int N, int K) {
        int[][] edges = new int[N + 1][N + 1];
        List<Integer> g[] = new ArrayList[N + 1];
        for (int i = 1;i <= N;i++) g[i] = new ArrayList<>();
        for (int[] time : times) {
            int u = time[0];
            int v = time[1];
            int w = time[2];
            edges[u][v] = w;
            g[u].add(v);
        }

        
        Queue<Integer> q = new LinkedList<>();
        boolean[] visited = new boolean[N + 1];
        visited[K] = true;
        q.add(K);
        int time[] = new int[N + 1];
        while (!q.isEmpty()) {
            int u = q.poll();
            for (int v : g[u]) {
                if (!visited[v] || time[v] > time[u] + edges[u][v]) {
                    visited[v] = true;
                    q.add(v);
                    time[v] = time[u] + edges[u][v];
                }
            }
        }
        int ans = 0;
        for (int i = 1;i <= N;i++) {
            if (!visited[i]) return -1;
            ans = Math.max(ans, time[i]);
        }
        return ans;
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-23 001711](https://user-images.githubusercontent.com/73281015/213934072-640de2b2-d2ae-4875-9883-29c812375db2.png)

