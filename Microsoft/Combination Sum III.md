(Leetcode Problem)

Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

Only numbers 1 through 9 are used.
Each number is used at most once.
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

Example 1
Input: k = 3, n = 7
Output: [[1,2,4]]
Explanation:
1 + 2 + 4 = 7
There are no other valid combinations.


CODE (JAVA) :
```
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
       List<List<Integer>> result = new ArrayList<>();
        combinations(1, k, n, new LinkedList(), result);
        return result;
    }
    private void combinations(int start, int k, int n, LinkedList ll, List<List<Integer>> result){
        if(k < 0 || n < 0) return;
        if(k == 0 && n == 0) {
            result.add(new ArrayList(ll));
            return;
        }
        for(int i= start; i <= 9; i++){
            ll.add(i);
            combinations(i+1, k-1, n-i, ll, result);
            ll.removeLast();
        }
    }
}
```
LEETCODE ACCEPTED : 
![Screenshot 2023-01-04 ](https://user-images.githubusercontent.com/73281015/210765579-e129236e-646c-4f39-840b-3234f490488f.png)
