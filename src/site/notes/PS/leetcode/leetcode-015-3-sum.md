---
{"dg-path":"/ps/leetcode/3-sum","dg-publish":true,"permalink":"//ps/leetcode/3-sum/","dgPassFrontmatter":true,"dg-note-properties":{}}
---

## 개요
- 문제:
	- https://leetcode.com/problems/3sum/description/
- 풀이:
	- 
- 기록:
	- 고정 하나를 두고 two sum을 하는 것 까지는 착안을 했는데, 중복을 어떻게 제거할지에서 막혔음
	- 풀이를 보니 set을 쓰기보단 정렬을 해서 작은 수부터 무조건 정렬된 답이 나올테니, 인덱스 한 개 전과 비교해서 동일한 값인지 아닌지를 비교하는 식으로 중복을 처리 했음
	- 정렬 알고리즘 전반 적으로 정리가 필요한 것 같음. 안정, 불안정 정렬은 뭔지, 퀵정렬은 어떤 정렬 방식인지 등

## 정답 코드
- 제미나이 정답 코드
	```java
	class Solution {
		public List<List<Integer>> threeSum(int[] nums) {
			Arrays.sort(nums); // Dual-Pivot Quicksort
			List<List<Integer>> result = new ArrayList<>();

			for (int i = 0; i < nums.length - 2; i++) {
				// 중복된 기준값 건너뛰기 (이전 값과 같으면 이미 처리했음)
				if (i > 0 && nums[i] == nums[i - 1])
					continue;

				int left = i + 1;
				int right = nums.length - 1;

				while (left < right) {
					int sum = nums[i] + nums[left] + nums[right];

					if (sum == 0) {
						result.add(Arrays.asList(nums[i], nums[left], nums[right]));

						// 정답을 찾은 후에도 중복된 요소 건너뛰기 (핵심)
						while (left < right && nums[left] == nums[left + 1])
							left++;
						while (left < right && nums[right] == nums[right - 1])
							right--;

						left++;
						right--;
					} else if (sum < 0) {
						left++; // 합이 0보다 작으므로 더 큰 값을 찾아야 함 (정렬됨)
					} else {
						right--; // 합이 0보다 크므로 더 작은 값을 찾아야 함
					}
				}
			}
			return result;
		}
	}
	```
	- 
- 다른 사람 제출 코드