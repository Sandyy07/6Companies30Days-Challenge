(Leetcode Problem) 

In LeetCode Store, there are n items to sell. Each item has a price. However, there are some special offers, and a special offer consists of one or more different kinds of items with a sale price.

You are given an integer array price where price[i] is the price of the ith item, and an integer array needs where needs[i] is the number of pieces of the ith item you want to buy.

You are also given an array special where special[i] is of size n + 1 where special[i][j] is the number of pieces of the jth item in the ith offer and special[i][n] (i.e., the last integer in the array) is the price of the ith offer.

Return the lowest price you have to pay for exactly certain items as given, where you could make optimal use of the special offers. You are not allowed to buy more items than you want, even if that would lower the overall price. You could use any of the special offers as many times as you want.

 

Example 1:

Input: price = [2,5], special = [[3,0,5],[1,2,10]], needs = [3,2]
Output: 14
Explanation: There are two kinds of items, A and B. Their prices are $2 and $5 respectively. 
In special offer 1, you can pay $5 for 3A and 0B
In special offer 2, you can pay $10 for 1A and 2B. 
You need to buy 3A and 2B, so you may pay $10 for 1A and 2B (special offer #2), and $4 for 2A.


CODE (JAVA) :

```
class Solution {
    Map<List<Integer>,Integer>map=new HashMap<>();
    List<Integer>price;
    List<List<Integer>>special;
    public int shoppingOffers(List<Integer> price, List<List<Integer>> special, List<Integer> needs) {
        this.price=price;
        this.special=special;
        List<Integer>empty=new ArrayList<>();
        for(int i=0;i<price.size();i++)empty.add(0);
        map.put(empty,0);
        return dfs(needs);
    }
    public int dfs(List<Integer>needs){
        if(map.containsKey(needs))return map.get(needs);
        int res=calculate(needs);
        for(int i=0;i<special.size();i++){
            List<Integer>remain=subtract(needs,special.get(i));
            if(remain!=null){
                res=Math.min(res,special.get(i).get(special.get(i).size()-1)+dfs(remain));
            }
        }
        map.put(needs,res);
        return res;
    }
    public List<Integer> subtract(List<Integer>needs,List<Integer>offers){
        List<Integer>list=new ArrayList<>();
        for(int i=0;i<needs.size();i++){
            if(offers.get(i)>needs.get(i))return null;
            list.add(needs.get(i)-offers.get(i));
        }
        return list;
    }
    public int calculate(List<Integer>needs){
        int sum=0;
        for(int i=0;i<needs.size();i++){
            sum+=(needs.get(i)*price.get(i));
        }
        return sum;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-16 125456](https://user-images.githubusercontent.com/73281015/212620590-abccabf7-d46b-409a-88ad-cad16696812b.png)

