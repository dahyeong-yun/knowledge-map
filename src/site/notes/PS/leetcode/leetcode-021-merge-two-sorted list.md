---
{"dg-path":"/ps/leetcode/merge-two-sorted-list","dg-publish":true,"permalink":"//ps/leetcode/merge-two-sorted-list/","dgPassFrontmatter":true,"dg-note-properties":{}}
---

## 개요
- 문제: https://leetcode.com/problems/merge-two-sorted-lists/description/
- 풀이: https://gemini.google.com/share/4edaea5deece


## 정답 코드
- 제미나이 정답 코드
    ```java
    /**
    * Definition for singly-linked list.
    * public class ListNode {
    * int val;
    * ListNode next;
    * ListNode() {}
    * ListNode(int val) { this.val = val; }
    * ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    * }
    */
    class Solution {
        public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
            // 1. Sentinel Node (Dummy) 생성
            // - 스택 메모리에 참조 변수만 생성, 힙에 실제 객체 생성
            ListNode dummy = new ListNode(-1);
            ListNode curr = dummy;

            // 2. 두 리스트 순회 (O(min(N, M)))
            while (list1 != null && list2 != null) {
                if (list1.val <= list2.val) {
                    curr.next = list1;   // 포인터만 연결 (데이터 복사 X)
                    list1 = list1.next;
                } else {
                    curr.next = list2;
                    list2 = list2.next;
                }
                curr = curr.next;
            }

            // 3. 남은 노드 연결 (O(1))
            // - 반복문이 끝났다는 것은 둘 중 하나는 끝났다는 뜻.
            // - 남은 리스트는 이미 정렬되어 있으므로 통째로 연결하면 됨.
            if (list1 != null) {
                curr.next = list1;
            } else if (list2 != null) {
                curr.next = list2;
            }

            return dummy.next; // 실제 헤드 반환
        }
    }
	```
	- 이 문제는 처음에 입력 부분의 ListNodea에 대한 설명을 잘 읽지 않아서, 해당 커스텀 자료구조를 활욜한 풀이로 넘어가지 못했다.
    - 풀이 자체는 커서를 사용해서 합려진 ListNode 자체를 반환하는 형태로 만들어져 있다.
- 다른 사람 제출 코드
