(Leetcode Problem) 

Alice manages a company and has rented some floors of a building as office space. Alice has decided some of these floors should be special floors, used for relaxation only.

You are given two integers bottom and top, which denote that Alice has rented all the floors from bottom to top (inclusive). You are also given the integer array special, where special[i] denotes a special floor that Alice has designated for relaxation.

Return the maximum number of consecutive floors without a special floor.

 

Example 1:

Input: bottom = 2, top = 9, special = [4,6]
Output: 3
Explanation: The following are the ranges (inclusive) of consecutive floors without a special floor:
- (2, 3) with a total amount of 2 floors.
- (5, 5) with a total amount of 1 floor.
- (7, 9) with a total amount of 3 floors.
Therefore, we return the maximum number which is 3 floors.


CODE (JAVA) :

```
class Solution {
    public int maxConsecutive(int bottom, int top, int[] special) {
        Arrays.sort(special);
        int ans=0; int s=bottom; int e=top;
        for(int i=0;i<special.length;i++){
           int si=special[i]-s;
            ans=Math.max(ans,si);
            s=special[i]+1;
        }
        return Math.max(ans,e-special[special.length-1]);
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-23 232756](https://user-images.githubusercontent.com/73281015/214114496-b28a2103-6902-4531-822c-95d191f13f83.png)

