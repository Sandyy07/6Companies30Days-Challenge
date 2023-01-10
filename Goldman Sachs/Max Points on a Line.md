(Leetcode Problem)

Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane, return the maximum number of points that lie on the same straight line.

 

Example 1:


Input: points = [[1,1],[2,2],[3,3]]
Output: 3

CODE (JAVA) :

```
class Solution {
public int maxPoints(int[][] points) {
int len = points.length;
if(len <= 2) return len;

    int max = 2;
	for(int i = 0; i < len; i++) {	
		for(int j = i + 1; j < len; j++) {
			int count = 0;
			
			long dxi = (long)points[j][0] - (long)points[i][0];
			long dyi = (long)points[j][1] - (long)points[i][1];				
			
			for(int k = 0; k < len; k++) {
					
				if(k == i || k == j) {
					continue;
				}
				
				long dxk = (long)points[k][0] - (long)points[i][0];
				long dyk = (long)points[k][1] - (long)points[i][1];
					
				if(dxi == 0 && dyi == 0) {
					if(dxk == 0 && dyk == 0) {
						count ++;
					}
					else {
						break;
					}
				}
				else {
					if(dxk * dyi - dyk * dxi == 0) {
						count ++;
					}
				}					
			}				
			
			max = Math.max(max, count + 2);
		}			
	}
    
    return max;
}
}

```
LEETCODE ACCEPTED :


![Screenshot 2023-01-10 124206](https://user-images.githubusercontent.com/73281015/211485168-c5c8030c-a8a0-49a0-8260-8fbbcb6690c3.png)

