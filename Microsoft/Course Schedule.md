(Leetcode Problem)

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. 
You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false.

Example 1
Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.

CODE (JAVA) :
```
  class Solution {
    public boolean canFinish(int n, int[][] p) {
        List<List<Integer>> nm=new ArrayList<>();
        for(int i=0;i<n;i++)
        {
            nm.add(new ArrayList<>());
        }
        for(int i=0;i<p.length;i++)
        {
            nm.get(p[i][0]).add(p[i][1]);
        }
        Queue<Integer> kk=new LinkedList<>();
        int a[]=new int[n];
        for(int i=0;i<n;i++)
        {
            for(int k:nm.get(i))
            {
                a[k]++;
            }
        }
        for(int i=0;i<a.length;i++)
        {
            if(a[i]==0)
            {
                kk.offer(i);
            }
        }
        List<Integer> k=new ArrayList<>();
        while(!kk.isEmpty())
        {
            int x=kk.poll();
            k.add(x);
            for(int j:nm.get(x))
            {
                a[j]--;
                if(a[j]==0)
                {
                    kk.offer(j);
                }
            }
        }
        return k.size()==n;
    }
}
```
LEETCODE ACCEPTED :

![Screenshot 2023-01-03 ](https://user-images.githubusercontent.com/73281015/210766331-8623a842-6a6b-4948-b5fa-65b009a06866.png)
