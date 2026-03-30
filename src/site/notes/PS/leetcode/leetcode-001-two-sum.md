---
{"dg-path":"ps/leetcode/two-sum","dg-publish":true,"permalink":"/ps/leetcode/two-sum/","dgPassFrontmatter":true,"noteIcon":"","created":"2026-02-03T19:05:19.897+09:00","updated":"2026-03-30T13:17:37.426+09:00","dg-note-properties":{}}
---

## 개요
- 문제:
	- https://leetcode.com/problems/two-sum/description/
- 질문:
	- https://gemini.google.com/share/d950fa8923c2


## 정답 코드
- 제미나이 정답 코드
    ```java
	class Solution {
		public int[] twoSum(int[] nums, int target) {
			Map<Integer, Integer> map = new HashMap<>();
			for (int i = 0; i < nums.length; i++) {
				if (map.containsKey(target - nums[i])) {
					return new int[]{map.get(target - nums[i]), i};
				}
				map.put(nums[i], i);
			}
			throw new IllegalArgumentException();
		}
	}
	```
	- 
- 다른 사람 제출 코드
