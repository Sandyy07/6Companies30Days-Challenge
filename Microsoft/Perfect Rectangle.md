(Leetcode Problem)

Given an array rectangles where rectangles[i] = [xi, yi, ai, bi] represents an axis-aligned rectangle. The bottom-left point of the rectangle is (xi, yi) and the top-right point of it is (ai, bi).

Return true if all the rectangles together form an exact cover of a rectangular region.

Example 1

Input: rectangles = [[1,1,3,3],[3,1,4,2],[3,2,4,4],[1,3,2,4],[2,3,3,4]]
Output: true
Explanation: All 5 rectangles together form an exact cover of a rectangular region.

```
CODE (JAVA) :
class Solution {
    public boolean isRectangleCover(int[][] rectangles) {
        int X1 = Integer.MAX_VALUE, 
        Y1 = Integer.MAX_VALUE, 
        X2 = Integer.MIN_VALUE, 
        Y2 = Integer.MIN_VALUE;
        
        Set<String> points = new HashSet<>();
        int actual_area = 0;
        
        for(int[] item : rectangles){
            int x1 = item[0], 
            y1 = item[1], 
            x2 = item[2], 
            y2 = item[3];
            
            X1 = Math.min(X1, x1);
            Y1 = Math.min(Y1, y1);
            X2 = Math.max(X2, x2);
            Y2 = Math.max(Y2, y2);
            
            actual_area += (x2-x1)*(y2-y1);
            int[] p1 = new int[]{x1,y1};int[] p2 = new int[]{x1,y2};
            int[] p3 = new int[]{x2,y1};int[] p4 = new int[]{x2,y2};
            for(int[] p : new int[][]{p1,p2,p3,p4}){
                String s = p[0] + "," + p[1];
                if(points.contains(s)){
                    points.remove(s);
                }else{
                    points.add(s);
                }
            }
        }
        int expected_area = (X2-X1)*(Y2-Y1);
        if(actual_area != expected_area){
            return false;
        }
        if(points.size() != 4) return false;
        String s1 = X1 + "," + Y1;
        String s2 = X1 + "," + Y2;
        String s3 = X2 + "," + Y1;
        String s4 = X2 + "," + Y2;
        if(!points.contains(s1)) return false;
        if(!points.contains(s2)) return false;
        if(!points.contains(s3)) return false;
        if(!points.contains(s4)) return false;
        return true;
    }
}
```

LEETCODE ACCEPTED :
![Screenshot 2023-01-05 ](https://user-images.githubusercontent.com/73281015/210767386-61511de5-5017-412d-8f2f-0ce20ec40245.png)
