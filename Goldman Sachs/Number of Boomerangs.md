(Leetcode Problem)

You are given n points in the plane that are all distinct, where points[i] = [xi, yi]. A boomerang is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (the order of the tuple matters).

Return the number of boomerangs.

 

Example 1:

Input: points = [[0,0],[1,0],[2,0]]
Output: 2
Explanation: The two boomerangs are [[1,0],[0,0],[2,0]] and [[1,0],[2,0],[0,0]].

CODE (JAVA) :

```
class Solution {
    public int numberOfBoomerangs(int[][] points) {
        HashMap<Integer,Integer> h=new HashMap<>();
        int ans=0;
        for(int i=0;i<points.length;i++){
            for(int j=0;j<points.length;j++){
                if(i==j) continue;
                int d=d(points[i],points[j]);
                h.put(d,h.getOrDefault(d,0)+1);
            }
            for(var x:h.values()){
                ans+=x*(x-1);
            }
            h.clear();
        }
        return ans;
    }

    int d(int i[],int j[]){
        int a=i[0]-j[0]; int b=i[1]-j[1];
        return a*a+b*b;
    }
}
```
LEETCODE ACCEPTED :

![Screenshot 2023-01-09 103910](https://user-images.githubusercontent.com/73281015/211244250-7be4279f-0c5f-49cf-a787-310b0fb3764b.png)
