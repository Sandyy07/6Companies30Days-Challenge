(Leetcode Problem) 

Given an array of strings words and an integer k, return the k most frequent strings.

Return the answer sorted by the frequency from highest to lowest. Sort the words with the same frequency by their lexicographical order.

 

Example 1:

Input: words = ["i","love","leetcode","i","love","coding"], k = 2
Output: ["i","love"]
Explanation: "i" and "love" are the two most frequent words.
Note that "i" comes before "love" due to a lower alphabetical order.


CODE (JAVA) :

```
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
//     Map <String ,Integer> m=new HashMap<>();
//         for(var w : words) m.put(w,m.getOrDefault(w,0)+1);
    
//     PriorityQueue<String> pq=new PriorityQueue<>(new Comparator<String>(){
//    public int compare(String w1 , String w2){
//             if(m.get(w1)==m.get(w2)) return w2.compareTo(w1);
//             return m.get(w1)-m.get(w2);
//     }
//     });

//     for(var e:m.entrySet()){
//         pq.add(e.getKey());
//         if(pq.size()>k) pq.poll();
//     }
//     List<String> ans=new  ArrayList<String>();
//     while(!pq.isEmpty()) ans.add(pq.poll());

//      Collections.reverse(ans);
//      return ans;



       HashMap<String, Integer> count = new HashMap<>();
    
    for (int i = 0; i < words.length; i++)
        count.put(words[i], count.getOrDefault(words[i], 0) + 1);
    PriorityQueue<String> q = new PriorityQueue<>(words.length, (a, b) -> count.get(a) == count.get(b) ? a.compareTo(b) : count.get(b) - count.get(a));
    List<String> res = new ArrayList<>();
    
    for (String key : count.keySet()) 
        q.add(key);
    
    for (int i = k - 1; i >= 0; i--) 
        res.add(q.poll());
    
    return res;
    }
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-30 112008](https://user-images.githubusercontent.com/73281015/215397506-088b8f23-fc3e-4be4-8706-e8848ab9a6d2.png)
