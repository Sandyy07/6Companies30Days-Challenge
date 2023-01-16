(Leetcode Problem) 

(This problem is an interactive problem.)

You may recall that an array arr is a mountain array if and only if:

arr.length >= 3
There exists some i with 0 < i < arr.length - 1 such that:
arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
arr[i] > arr[i + 1] > ... > arr[arr.length - 1]
Given a mountain array mountainArr, return the minimum index such that mountainArr.get(index) == target. If such an index does not exist, return -1.

You cannot access the mountain array directly. You may only access the array using a MountainArray interface:

MountainArray.get(k) returns the element of the array at index k (0-indexed).
MountainArray.length() returns the length of the array.
Submissions making more than 100 calls to MountainArray.get will be judged Wrong Answer. Also, any solutions that attempt to circumvent the judge will result in disqualification.

 

Example 1:

Input: array = [1,2,3,4,5,3,1], target = 3
Output: 2
Explanation: 3 exists in the array, at index=2 and index=5. Return the minimum index, which is 2.


CODE (JAVA) :

```
class Solution {
 public int findInMountainArray(int target, MountainArray arr) {
	var peak = getPeakIndex(arr);
	var idx = binarySearch(arr, 0, peak, target, true);
	return idx == -1 ? binarySearch(arr, peak + 1, arr.length() - 1, target, false) : idx;
}

private int getPeakIndex(MountainArray arr) {
	var low = 0;
	var high = arr.length() - 1;

	while (low < high) {
		var mid = low + (high - low) / 2;
		if (arr.get(mid) > arr.get(mid + 1))
			high = mid;
		else
			low = mid + 1;
	}
	return low;
}

private int binarySearch(MountainArray arr, int low, int high, int target, boolean isAscending) {
	while (low <= high) {
		var mid = low + (high - low) / 2;
		if (arr.get(mid) == target)
			return mid;
		if (isAscending) {
			if (arr.get(mid) < target)
				low = mid + 1;
			else
				high = mid - 1;
		} else {
			if (arr.get(mid) < target)
				high = mid - 1;
			else
				low = mid + 1;
		}
	}
	return -1;
}
}

```
LEETCODE ACCEPTED :

![Screenshot 2023-01-16 223459](https://user-images.githubusercontent.com/73281015/212732654-7e79d679-2508-49d7-af73-26a66df9dba8.png)
