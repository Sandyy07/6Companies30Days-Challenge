(Leetcode Problem)

You are given an integer array cards where cards[i] represents the value of the ith card. A pair of cards are matching if the cards have the same value.

Return the minimum number of consecutive cards you have to pick up to have a pair of matching cards among the picked cards. If it is impossible to have matching cards, return -1.

 

Example 1:

Input: cards = [3,4,2,3,4,7]
Output: 4
Explanation: We can pick up the cards [3,4,2,3] which contain a matching pair of cards with value 3. Note that picking up the cards [4,2,3,4] is also optimal.

CODE (JAVA) :

 ```
 class Solution {
    public int minimumCardPickup(int[] cards) {
        int min=Integer.MAX_VALUE;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<cards.length;i++){
            if(hm.containsKey(cards[i])){
                int l=hm.get(cards[i]);
                min=Math.min(min,i-l+1);
            }
            hm.put(cards[i],i);
        }
        return min==Integer.MAX_VALUE?-1:min;
    }
}
 ```
LEETCODE ACCEPTED :

![Screenshot 2023-01-09 224424](https://user-images.githubusercontent.com/73281015/211367366-30cf36b9-5cc5-4150-906e-0a8b5efdf05d.png)
