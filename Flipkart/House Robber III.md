(Leetcode Problem) 

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called root.

Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that all houses in this place form a binary tree. It will automatically contact the police if two directly-linked houses were broken into on the same night.

Given the root of the binary tree, return the maximum amount of money the thief can rob without alerting the police.

 
Example 1:


Input: root = [3,2,3,null,3,null,1]
Output: 7
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.


CODE (JAVA) :

```
class Solution {
    public int rob(TreeNode root) {
        return s( root , new HashMap<>());
    }

    int s(TreeNode r , HashMap<TreeNode , Integer> m){
        if(r==null) return 0;
        if(m.containsKey(r)) return m.get(r);
        int v=0;
        if(r.left!=null) v+=s(r.left.left,m)+s(r.left.right,m);
        if(r.right!=null) v+=s(r.right.left,m)+s(r.right.right,m);

        v=Math.max(v+r.val, s(r.left , m)+ s(r.right,m));
        m.put(r,v);
        return v;
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-17 154223](https://user-images.githubusercontent.com/73281015/212870989-a79a1f3e-2a76-42f1-86e1-a687402a5561.png)
