(Leetcode Problem) 
You are given two string arrays creators and ids, and an integer array views, all of length n. The ith video on a platform was created by creator[i], has an id of ids[i], and has views[i] views.

The popularity of a creator is the sum of the number of views on all of the creator's videos. Find the creator with the highest popularity and the id of their most viewed video.

If multiple creators have the highest popularity, find all of them.
If multiple videos have the highest view count for a creator, find the lexicographically smallest id.
Return a 2D array of strings answer where answer[i] = [creatori, idi] means that creatori has the highest popularity and idi is the id of their most popular video. The answer can be returned in any order.

 

Example 1:

Input: creators = ["alice","bob","alice","chris"], ids = ["one","two","three","four"], views = [5,10,5,4]
Output: [["alice","one"],["bob","two"]]
Explanation:
The popularity of alice is 5 + 5 = 10.
The popularity of bob is 10.
The popularity of chris is 4.
alice and bob are the most popular creators.
For bob, the video with the highest view count is "two".
For alice, the videos with the highest view count are "one" and "three". Since "one" is lexicographically smaller than "three", it is included in the answer.



CODE (JAVA) :

```
class Solution {
 public List<List<String>> mostPopularCreator(String[] creators, String[] ids, int[] views) {
    Map<String, Queue<Node>> map = new HashMap<>();
    Map<String, Long> cntMap = new HashMap<>();
    long max = 0;
    for(int i=0;i<creators.length;i++){
        map.putIfAbsent(creators[i], new PriorityQueue<>((a, b) -> a.view == b.view ? a.id.compareTo(b.id) : b.view - a.view));
        map.get(creators[i]).offer(new Node(ids[i], views[i]));
        cntMap.put(creators[i], cntMap.getOrDefault(creators[i], 0L) + views[i]);
        max = Math.max(max, cntMap.get(creators[i]));
    }
    List<List<String>> res = new ArrayList<>();
    for(Map.Entry<String, Long> e : cntMap.entrySet()) {
        if(e.getValue() == max) {
            res.add(Arrays.asList(e.getKey(), map.get(e.getKey()).poll().id));
        }
    }
    return res;
}

class Node {
    String id;
    int view;
    public Node(String id, int view) {
        this.id = id;
        this.view = view;
    }
    
    @Override
    public String toString() {
        return id + "," + view;
    }
}
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-30 104908](https://user-images.githubusercontent.com/73281015/215393496-72f15cd7-a115-45e1-a768-295785010ad8.png)
