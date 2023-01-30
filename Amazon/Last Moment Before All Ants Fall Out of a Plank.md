(Leetcode Problem) 

We have a wooden plank of the length n units. Some ants are walking on the plank, each ant moves with a speed of 1 unit per second. Some of the ants move to the left, the other move to the right.

When two ants moving in two different directions meet at some point, they change their directions and continue moving again. Assume changing directions does not take any additional time.

When an ant reaches one end of the plank at a time t, it falls out of the plank immediately.

Given an integer n and two integer arrays left and right, the positions of the ants moving to the left and the right, return the moment when the last ant(s) fall out of the plank.

 

Example 1:


Input: n = 4, left = [4,3], right = [0,1]
Output: 4
Explanation: In the image above:
-The ant at index 0 is named A and going to the right.
-The ant at index 1 is named B and going to the right.
-The ant at index 3 is named C and going to the left.
-The ant at index 4 is named D and going to the left.
The last moment when an ant was on the plank is t = 4 seconds. After that, it falls immediately out of the plank. (i.e., We can say that at t = 4.0000000001, there are no ants on the plank).


CODE (JAVA) :

```
class Solution {
    public int getLastMoment(int n, int[] left, int[] right) {

            if(n==0 || (left.length==0 && right.length==0))
       return 0;
    
    int maxLeft=0;
    int minRight=n;
    for(int l:left) {
        if(l>maxLeft)
            maxLeft=l;
    }
    
    for(int r:right) {
        if(r<minRight)
            minRight=r;
    }
        
    return Math.max(maxLeft,n-minRight);
        // int l=0; int r=Integer.MAX_VALUE;
        // for(var v:left) l=Math.max(l,v);
        // for(var v:left) r=Math.min(r,v);
        // return Math.max(l,n-r);
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-30 113333](https://user-images.githubusercontent.com/73281015/215399231-7eef1cad-56a9-490f-ae19-957ca53e55bb.png)

