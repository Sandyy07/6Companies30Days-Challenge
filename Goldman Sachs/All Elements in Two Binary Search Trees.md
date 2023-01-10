(Leetcode Problem)

Given two binary search trees root1 and root2, return a list containing all the integers from both trees sorted in ascending order.

 

Example 1:


Input: root1 = [2,1,4], root2 = [1,0,3]
Output: [0,1,1,2,3,4]

CODE (JAVA) :

```
class Solution {
public List getAllElements(TreeNode root1, TreeNode root2) {

     List<Integer> res = new ArrayList<>();
    
      inorder(root1 ,res);
      inorder(root2 ,res);
   
      Collections.sort(res);
    
       return res;
    
}
static void inorder(TreeNode root , List<Integer> ls){
    if(root == null){
        return;
    }
    inorder(root.left, ls);
    ls.add(root.val);
    inorder(root.right, ls);          
}
}
```
LEETCODE ACCEPTED :

![Screenshot 2023-01-10 123828](https://user-images.githubusercontent.com/73281015/211484516-bf3e6ebb-fbba-4486-b16b-4be1aa1a7f12.png)
