(Leetcode Problem) 

Given the head of a linked list, we repeatedly delete consecutive sequences of nodes that sum to 0 until there are no such sequences.

After doing so, return the head of the final linked list.  You may return any such answer.

 

(Note that in the examples below, all sequences are serializations of ListNode objects.)

Example 1:

Input: head = [1,2,-3,3,1]
Output: [3,1]
Note: The answer [1,2,1] would also be accepted.


CODE (JAVA) :

```
class Solution {
public ListNode removeZeroSumSublists(ListNode head) {
	HashMap<Integer, ListNode> mp = new HashMap<>();
	ListNode xx = new ListNode(0);
	xx.next = head;
	mp.put(0, xx);
	int sum = 0;
	while (head != null) {
		sum += head.val;
		if (mp.containsKey(sum)) {
			ListNode front = mp.get(sum).next;
			int val = sum;
			while (front != head) {
				val += front.val;
				mp.remove(val);
				front = front.next;
			}
			mp.get(sum).next = head.next;
			head.next = null;
			head = mp.get(sum).next;
		}
		else {
			mp.put(sum, head);
			head = head.next;
		}
	}
	return xx.next;
}
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-16 125456](https://user-images.githubusercontent.com/73281015/212673340-243ecc35-3b9c-41d8-b6af-1fecae17caf0.png)
