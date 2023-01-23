


(Leetcode Problem) 

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

 

Example 1:

Input: fruits = [1,2,1]
Output: 3
Explanation: We can pick from all 3 trees.


CODE (JAVA) :

```
class Solution {
    public int totalFruit(int[] fruits) {
         int i=0,j=0,max=0;
                        HashMap<Integer ,Integer> hm=new HashMap<>();
            while(j<fruits.length){
                hm.put(fruits[j], hm.getOrDefault(fruits[j], 0)+1);
                if(hm.size()<2) {
                      j++;
                     max=j;
                }
                  
                else if (hm.size()==2) {
                    max=Math.max(max, j-i+1);
                    j++;
                }
                else if (hm.size()>2) {
                    while(hm.size()>2){
                        hm.put(fruits[i], hm.get(fruits[i])-1);
                        if(hm.get(fruits[i])==0) hm.remove(fruits[i]);
                        i++;
                    }
                    j++;
                }
            }
            return max;
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-23 200007](https://user-images.githubusercontent.com/73281015/214064987-0817617c-a239-4423-842a-cc558b6dae1e.png)





