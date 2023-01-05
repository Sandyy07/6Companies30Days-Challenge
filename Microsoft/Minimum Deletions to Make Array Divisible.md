(Leetcode Problem)
You are given two positive integer arrays nums and numsDivide. You can delete any number of elements from nums.

Return the minimum number of deletions such that the smallest element in nums divides all the elements of numsDivide. If this is not possible, return -1.

Note that an integer x divides y if y % x == 0.

 

Example 1:

Input: nums = [2,3,2,4,3], numsDivide = [9,6,9,3,15]
Output: 2
Explanation: 
The smallest element in [2,3,2,4,3] is 2, which does not divide all the elements of numsDivide.
We use 2 deletions to delete the elements in nums that are equal to 2 which makes nums = [3,4,3].
The smallest element in [3,4,3] is 3, which divides all the elements of numsDivide.
It can be shown that 2 is the minimum number of deletions needed.

CODE (JAVA) :

```
class Solution {
    public int minOperations(int[] nums, int[] numsDivide) {
           int val=numsDivide[0];
        for(int i=1;i<numsDivide.length;i++)
        {
          int ngcd = gcd(val,numsDivide[i]);
          val=ngcd;  
        }
        Arrays.sort(nums);
        
        for(int i=0;i<nums.length;i++)
        {
            if(val%nums[i] == 0)
            {
                return i;
            }
        }
        return -1;
    }
    
    public int gcd(int a,int b)
    {
        if(b==0)
        {
            return a;
        }
        else
        {
           return gcd(b,a%b);    
        }
        
    }
}
```
LEETCODE ACCEPTED :
![Screenshot 2023-01-05](https://user-images.githubusercontent.com/73281015/210772683-9579c168-6ef9-4816-9441-42460a1346d6.png)
