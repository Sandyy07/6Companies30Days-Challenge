
  
  (Leetcode Problem)
There is an undirected tree with n nodes labeled from 0 to n - 1, rooted at node 0. You are given a 2D integer array edges of length n - 1 where edges[i] = [ai, bi] indicates that there is an edge between nodes ai and bi in the tree.

At every node i, there is a gate. You are also given an array of even integers amount, where amount[i] represents:

the price needed to open the gate at node i, if amount[i] is negative, or,
the cash reward obtained on opening the gate at node i, otherwise.
The game goes on as follows:

Initially, Alice is at node 0 and Bob is at node bob.
At every second, Alice and Bob each move to an adjacent node. Alice moves towards some leaf node, while Bob moves towards node 0.
For every node along their path, Alice and Bob either spend money to open the gate at that node, or accept the reward. Note that:
If the gate is already open, no price will be required, nor will there be any cash reward.
If Alice and Bob reach the node simultaneously, they share the price/reward for opening the gate there. In other words, if the price to open the gate is c, then both Alice and Bob pay c / 2 each. Similarly, if the reward at the gate is c, both of them receive c / 2 each.
If Alice reaches a leaf node, she stops moving. Similarly, if Bob reaches node 0, he stops moving. Note that these events are independent of each other.
Return the maximum net income Alice can have if she travels towards the optimal leaf node.

CODE (JAVA) :

```
class Solution {
public int mostProfitablePath(int[][] edges, int bob, int[] amount) {
        int n = amount.length;
        List<List<Integer>> adjList = new ArrayList<>();
        
        for(int i=0; i<n; i++){
            adjList.add(new ArrayList<>());
        }
        
        
        for(int [] edge:edges){
            adjList.get(edge[0]).add(edge[1]);
            adjList.get(edge[1]).add(edge[0]);
        }
        
        HashMap<Integer, Integer> map = new HashMap<>();
        boolean [] visited = new boolean[n];
        
        dfs(bob, 0, 0, adjList, visited, map);
        
        visited = new boolean[n];
        
        Queue<int[]> queue = new LinkedList<>();
        
        queue.add(new int[]{0, 0, 0}); 
        
        int ans = Integer.MIN_VALUE;
        
        while(!queue.isEmpty()){
            int src = queue.peek()[0];
            int time = queue.peek()[1];
            int income = queue.peek()[2];
            queue.poll();
            
            visited[src] = true;
            
            if(map.get(src) == null){
                income += amount[src];
            }
            else{
                if(time < map.get(src)){
                    income += amount[src];
                }
                else if(time == map.get(src)){
                    income += amount[src]/2;
                }
            }
            
            if(src!=0 && adjList.get(src).size() == 1){
                ans = Math.max(ans, income);
            }
            
            for(Integer adjNode: adjList.get(src)){
                if(!visited[adjNode]){
                    queue.add(new int[]{adjNode, time+1, income});
                }
            }
            
        }
        
        return ans;
    }
    
    private boolean dfs(int src, int target, int time, List<List<Integer>> adjList, boolean [] visited, HashMap<Integer, Integer> map){
        visited[src] = true;
        map.put(src, time);
        
        if(src == target){
            return true;
        }
        
        for(Integer adjNode : adjList.get(src)){
            if(!visited[adjNode]){
                if(dfs(adjNode, target, time+1, adjList, visited, map)){
                    return true;
                }
            }
        }
        
        map.remove(src);
        return false;
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-05](https://user-images.githubusercontent.com/73281015/210768591-2d8de5e6-6cc2-4e25-9e46-fae9f4e52fce.png)
