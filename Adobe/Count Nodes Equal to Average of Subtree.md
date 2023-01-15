
(Leetcode Problem) 

Given the root of a binary tree, return the number of nodes where the value of the node is equal to the average of the values in its subtree.

Note:

The average of n elements is the sum of the n elements divided by n and rounded down to the nearest integer.
A subtree of root is a tree consisting of root and all of its descendants.
 

Example 1:


Input: root = [4,8,5,0,1,null,6]
Output: 5
Explanation: 
For the node with value 4: The average of its subtree is (4 + 8 + 5 + 0 + 1 + 6) / 6 = 24 / 6 = 4.
For the node with value 5: The average of its subtree is (5 + 6) / 2 = 11 / 2 = 5.
For the node with value 0: The average of its subtree is 0 / 1 = 0.
For the node with value 1: The average of its subtree is 1 / 1 = 1.
For the node with value 6: The average of its subtree is 6 / 1 = 6.




CODE (JAVA) :

```
public class Pair{
    int f,s;
    Pair(int f, int s){
        this.f = f;
        this.s = s;
    }
}

class Solution {

    int count;
    public int averageOfSubtree(TreeNode root) {
        count = 0;
        isAverageBT(root);
        return count;
    }

    public Pair isAverageBT(TreeNode root){
        if(root==null){
            return new Pair(0,0);
        }
        Pair left = isAverageBT(root.left);
        Pair right = isAverageBT(root.right);
        int sum = root.val + left.f + right.f;
        int number = 1 + left.s + right.s;
        if(sum/number == root.val){
            count++;
        } 
        return new Pair(sum,number);
    }

}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-15 182548](https://user-images.githubusercontent.com/73281015/212541952-cf98758b-878b-4c07-b51a-d3316f306bf9.png)
