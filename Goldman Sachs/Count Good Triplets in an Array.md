(Leetcode Problem)
You are given two 0-indexed arrays nums1 and nums2 of length n, both of which are permutations of [0, 1, ..., n - 1].

A good triplet is a set of 3 distinct values which are present in increasing order by position both in nums1 and nums2. In other words, if we consider pos1v as the index of the value v in nums1 and pos2v as the index of the value v in nums2, then a good triplet will be a set (x, y, z) where 0 <= x, y, z <= n - 1, such that pos1x < pos1y < pos1z and pos2x < pos2y < pos2z.

Return the total number of good triplets.

 

Example 1:

Input: nums1 = [2,0,1,3], nums2 = [0,1,2,3]
Output: 1
Explanation: 
There are 4 triplets (x,y,z) such that pos1x < pos1y < pos1z. They are (2,0,1), (2,0,3), (2,1,3), and (0,1,3). 
Out of those triplets, only the triplet (0,1,3) satisfies pos2x < pos2y < pos2z. Hence, there is only 1 good triplet.

CODE (JAVA) :

 ```
 class Solution {
    public long goodTriplets(int[] nums1, int[] nums2) {
        int n=nums1.length;
        int []pos = new int[n];
        
        FenwickTree ft = new FenwickTree(n+1);
        
        for(int i=0;i<n;i++)
            pos[nums2[i]]=i;
        
        long []left=new long[n];
        long []right = new long[n];
        
        for(int i=0;i<n;i++){
            int idx = pos[nums1[i]];
            left[i] = ft.sum(idx-1);
            ft.update(idx,1);
        }
        
        ft=new FenwickTree(n+1);
        
        for(int i=n-1;i>=0;i--){
            int idx = pos[nums1[i]];
            right[i]= ft.sum(n+1)-ft.sum(idx);
            ft.update(idx,1);
        }
        
        long ans=0;
        
        for (int i=0;i<n;i++)
            ans+= left[i]*right[i];
        
        return ans;
    }
}

class FenwickTree {
    int[] bit;
    int n;
    
    FenwickTree(int n) {
        this.n = n;
        this.bit = new int[n + 2];
    }
    
    public void update(int i, int val) {
        i++;
        while (i < bit.length) {
            bit[i] += val;
            i += (i & (-i));
        }
    }
    
    public int sum(int i) {
        int sum = 0;
        i++;
        while (i > 0) {
            sum += bit[i];
            i -= (i & (-i));
        }
        return sum;
    }
}
 ```
LEETCODE ACCEPTED :

![Screenshot 2023-01-10 012949](https://user-images.githubusercontent.com/73281015/211397083-30445705-48ca-4a75-aa59-343adc1ae6ef.png)
