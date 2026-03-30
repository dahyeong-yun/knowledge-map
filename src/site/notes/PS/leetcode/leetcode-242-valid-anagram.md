---
{"dg-path":"ps/leetcode/valid-anagram","dg-publish":true,"permalink":"/ps/leetcode/valid-anagram/","dgPassFrontmatter":true,"noteIcon":"","created":"2026-02-03T21:38:35.359+09:00","updated":"2026-03-30T13:17:33.726+09:00","dg-note-properties":{}}
---

## 개요
- 문제: https://leetcode.com/problems/valid-anagram/description/


## 정답 코드
- 제미나이 정답 코드
    ```java
    class Solution {
        public boolean isAnagram(String s, String t) {
            IntStream charS = s.chars();
            IntStream charT = t.chars();
            int[] arrayS = charS.sorted().toArray();
            int[] arrayT = charT.sorted().toArray();
            return Arrays.equals(arrayS, arrayT);
        }
    }
	```
	- 
- 다른 사람 제출 코드
