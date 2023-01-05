(Leetcode Problem)
You are given two 0-indexed integer arrays nums1 and nums2, each of size n, and an integer diff. Find the number of pairs (i, j) such that:

0 <= i < j <= n - 1 and
nums1[i] - nums1[j] <= nums2[i] - nums2[j] + diff.
Return the number of pairs that satisfy the conditions.

 

Example 1:

Input: nums1 = [3,2,5], nums2 = [2,2,1], diff = 1
Output: 3
Explanation:
There are 3 pairs that satisfy the conditions:
1. i = 0, j = 1: 3 - 2 <= 2 - 2 + 1. Since i < j and 1 <= 1, this pair satisfies the conditions.
2. i = 0, j = 2: 3 - 5 <= 2 - 1 + 1. Since i < j and -2 <= 2, this pair satisfies the conditions.
3. i = 1, j = 2: 2 - 5 <= 2 - 1 + 1. Since i < j and -3 <= 2, this pair satisfies the conditions.
Therefore, we return 3.

CODE (JAVA) :
class Solution {
     public long numberOfPairs(int[] nums1, int[] nums2, int diff) {
        int n = nums1.length;
        List<Integer> diffList = new ArrayList<>();
        long res = 0;
        for (int i = 0; i < n; i++) {
            int curDiff = nums1[i] - nums2[i];
            int target  = curDiff + diff; 
            res += countSmallerEqual(diffList, target);
            diffList.add((int) countSmallerEqual(diffList, curDiff), curDiff);
        }
        return res;
    }
    
    private long countSmallerEqual(List<Integer> diffList, int target) {
        int left = 0, right = diffList.size(); 
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (diffList.get(mid) <= target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return (long)left;
    }
}
LEETCODE ACCEPTED :

![Screenshot 2023-01-04 ](https://user-images.githubusercontent.com/73281015/210770778-1bd1eb9f-b1da-4de7-844b-5d039fa95354.png)
