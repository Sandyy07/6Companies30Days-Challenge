(Leetcode Problem) 

A social media company is trying to monitor activity on their site by analyzing the number of tweets that occur in select periods of time. These periods can be partitioned into smaller time chunks based on a certain frequency (every minute, hour, or day).

For example, the period [10, 10000] (in seconds) would be partitioned into the following time chunks with these frequencies:

Every minute (60-second chunks): [10,69], [70,129], [130,189], ..., [9970,10000]
Every hour (3600-second chunks): [10,3609], [3610,7209], [7210,10000]
Every day (86400-second chunks): [10,10000]
Notice that the last chunk may be shorter than the specified frequency's chunk size and will always end with the end time of the period (10000 in the above example).

Design and implement an API to help the company with their analysis.

Implement the TweetCounts class:

TweetCounts() Initializes the TweetCounts object.
void recordTweet(String tweetName, int time) Stores the tweetName at the recorded time (in seconds).
List<Integer> getTweetCountsPerFrequency(String freq, String tweetName, int startTime, int endTime) Returns a list of integers representing the number of tweets with tweetName in each time chunk for the given period of time [startTime, endTime] (in seconds) and frequency freq.
freq is one of "minute", "hour", or "day" representing a frequency of every minute, hour, or day respectively.
 

Example:

Input
["TweetCounts","recordTweet","recordTweet","recordTweet","getTweetCountsPerFrequency","getTweetCountsPerFrequency","recordTweet","getTweetCountsPerFrequency"]
[[],["tweet3",0],["tweet3",60],["tweet3",10],["minute","tweet3",0,59],["minute","tweet3",0,60],["tweet3",120],["hour","tweet3",0,210]]

Output
[null,null,null,null,[2],[2,1],null,[4]]

Explanation
TweetCounts tweetCounts = new TweetCounts();
tweetCounts.recordTweet("tweet3", 0);                              // New tweet "tweet3" at time 0
tweetCounts.recordTweet("tweet3", 60);                             // New tweet "tweet3" at time 60
tweetCounts.recordTweet("tweet3", 10);                             // New tweet "tweet3" at time 10
tweetCounts.getTweetCountsPerFrequency("minute", "tweet3", 0, 59); // return [2]; chunk [0,59] had 2 tweets
tweetCounts.getTweetCountsPerFrequency("minute", "tweet3", 0, 60); // return [2,1]; chunk [0,59] had 2 tweets, chunk [60,60] had 1 tweet
tweetCounts.recordTweet("tweet3", 120);                            // New tweet "tweet3" at time 120
tweetCounts.getTweetCountsPerFrequency("hour", "tweet3", 0, 210);  // return [4]; chunk [0,210] had 4 tweets


CODE (JAVA) :

```
class TweetCounts {
    Map<String, List<Integer>> map;
    public TweetCounts() {
        map = new HashMap<>();
    }
    
    public void recordTweet(String tweetName, int time) {
        map.putIfAbsent(tweetName, new ArrayList<>());
        map.get(tweetName).add(time);
    }
    
    public List<Integer> getTweetCountsPerFrequency(String freq, String tweetName, int startTime, int endTime) {
        List<Integer> times = map.get(tweetName);
        Collections.sort(times);
        List<Integer> res = new ArrayList<>();
        Map<Integer, Integer> m = new HashMap<>();
        if (freq.equals("hour")) {
            for (int i = 0; i < times.size(); i++) {
                if (times.get(i) >= startTime && times.get(i) <= endTime) {
                    int index = (times.get(i) - startTime) / 3600;
                    m.put(index, m.getOrDefault(index, 0) + 1);
                }
            }
            int count = 0;
            for (int i = startTime; i <= endTime; i += 3600) {
                res.add(m.getOrDefault(count++, 0));
            }
        } else if (freq.equals("minute")) {
            for (int i = 0; i < times.size(); i++) {
                if (times.get(i) >= startTime && times.get(i) <= endTime) {
                    int index = (times.get(i) - startTime) / 60;
                    m.put(index, m.getOrDefault(index, 0) + 1);
                }
                
            }
            int count = 0;
            for (int i = startTime; i <= endTime; i += 60) {
                res.add(m.getOrDefault(count++, 0));
            }
        } else {
            for (int i = 0; i < times.size(); i++) {
                if (times.get(i) >= startTime && times.get(i) <= endTime) {
                    int index = (times.get(i) - startTime) / (3600 * 24);
                    m.put(index, m.getOrDefault(index, 0) + 1);
                }
            }
            int count = 0;
            for (int i = startTime; i <= endTime; i += (3600 * 24)) {
                res.add(m.getOrDefault(count++, 0));
            }
        }
        return res;
    }
}


```
LEETCODE ACCEPTED :


![Screenshot 2023-01-30 095356](https://user-images.githubusercontent.com/73281015/215387263-5f1a8dbf-a9ee-4744-a4c9-1ebfcb5d908c.png)

