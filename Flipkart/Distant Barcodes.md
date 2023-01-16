(Leetcode Problem) 

In a warehouse, there is a row of barcodes, where the ith barcode is barcodes[i].

Rearrange the barcodes so that no two adjacent barcodes are equal. You may return any answer, and it is guaranteed an answer exists.

 

Example 1:

Input: barcodes = [1,1,1,2,2,2]
Output: [2,1,2,1,2,1]
Example 2:

Input: barcodes = [1,1,1,1,2,2,3,3]
Output: [1,3,1,3,1,2,1,2]


CODE (JAVA) :

```
class Solution {
    public int[] rearrangeBarcodes(int[] barcodes) {
        if(barcodes == null || barcodes.length == 0)
            return new int[0];
        Map<Integer, Integer> h = new HashMap<Integer, Integer>();
        for(int i: barcodes)
            h.put(i, h.getOrDefault(i, 0) + 1);
        PriorityQueue<Map.Entry<Integer, Integer>> pq = new PriorityQueue<Map.Entry<Integer, Integer>>(
		(a,b)->b.getValue()-a.getValue() == 0?a.getKey() - b.getKey(): b.getValue() - a.getValue());
        for(Map.Entry<Integer, Integer> entry:h.entrySet())
            pq.offer(entry);
        int[] res = new int[barcodes.length];
        int i = 0;
        while(!pq.isEmpty()) {
            int k = 2;
            List<Map.Entry> x = new ArrayList<Map.Entry>();
            while(k > 0 && !pq.isEmpty()) {
                Map.Entry<Integer, Integer> head = pq.poll();
                head.setValue(head.getValue() - 1);
                res[i++] = head.getKey();
                x.add(head);
                k--;
            }
            for(Map.Entry<Integer, Integer> e: x) {
                if(e.getValue() > 0) 
                    pq.add(e);
            }
            if(pq.isEmpty())
                break;
        }
        return res;
    }
}

```
LEETCODE ACCEPTED :
![Screenshot 2023-01-17 011637](https://user-images.githubusercontent.com/73281015/212755521-a21433c4-aff7-4637-94dd-4b04f0e32707.png)

