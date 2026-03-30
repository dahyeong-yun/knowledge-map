---
{"dg-path":"ps/leetcode/best-time-to-buy-and-sell-stock","dg-publish":true,"permalink":"/ps/leetcode/best-time-to-buy-and-sell-stock/","dgPassFrontmatter":true,"dg-note-properties":{}}
---

## 개요
- 문제
	- https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
- 질문
    - 
    
## 정답 코드
- 제미나이 정답 코드
    ```java
    class Solution {
        public int maxProfit(int[] prices) {
            // 1. 예외 처리: 데이터가 없거나 하루치만 있으면 거래 불가
            if (prices == null || prices.length < 2) {
                return 0;
            }

            // 2. 초기값 설정
            // minPrice: 지금까지 본 가격 중 가장 낮은 가격 (매수 후보)
            // Integer.MAX_VALUE로 초기화하여 첫 번째 값이 무조건 들어가게 함
            int minPrice = Integer.MAX_VALUE; 
            int maxProfit = 0; // 이익이 없으면 0 반환

            // 3. O(N) 순회
            for (int price : prices) {
                // Case A: 현재 가격이 역대 최저가보다 싸다면? -> 매수 시점을 갱신 (더 싸게 살 기회)
                if (price < minPrice) {
                    minPrice = price;
                } 
                // Case B: 현재 가격이 최저가보다 비싸다면? -> 지금 팔면 얼마인지 계산 (이익 실현 기회)
                else if (price - minPrice > maxProfit) {
                    maxProfit = price - minPrice;
                }
            }

            return maxProfit;
        }
    }
    ```
## 풀이 과정
- price 배열을 주고, 낮은 가격에 사서 높은 가격에 팔았을 때 얼마 이득인지를 물어보는 문제
- 가격 배열의 길이가 10만 이므로 10만의 제곱은 10,0 00,00 0,000 (100억) 이러면 O(N2) 으로는 못품
- O(NlogN)이면 10만 * 10의 2.5 승 = 10의 7.5승이면  대강 10의 8이라 쳤을때 10 00000000(10억)
	- 이것도 애매
- 그럼 결국 O(N) 으로 풀어야 함.

- loop 한번에 풀려면?
	- 투포인터?
	- 좌측 뒤로 다시 못가는 것이 핵심. 아러면 정렬도 못함
	- 그리고 뭐가 최대 값인지도 알아야함. 그럼 최대값을 임시 저장하고 계속 갱신하면서 포인터가 만나면 리턴하는 형식이 될 듯
	  - 근데 이러면 중복 루프가 됨.
	- 그러면 좌측 포인터가 다음 좌측 포인터 값보다 큰 경우 포인트를 계속 옮김. 이때 포인터가 우측 포인터와 만나면 0을 리턴. 그렇지 않고 작은 값을 찾았으면 우측 포인터를 좌측으로 옮김. 이때 계속 최대 값을 갱신. 이러다가 좌측 포인터와 만나면 최대 값을 리턴
		- 근데 무조건 좌측 포인터를 옮기는게 아니고 우측 포인터의 밸류보다 좌측 포인터의 밸류가 작았을 때 가야함.

```java
class Solution {
    public int maxProfit(int[] prices) {
        int left = 0;
        int right = prices.length - 1;   
        int result = 0;
				
        while(left < right) {
            if(prices[left] < prices[right]) {
                if(result < prices[right] - prices[left]) {
                    result = prices[right] - prices[left]; 
                }
                right--;
            }
						
            if(prices[left] > prices[right]) {
                left++;
            }
        }
        return result;
    }
}
```

- 1차 제출 후, 가격이 동일할 수 있음을 알았음 [3,3]
```java
class Solution {
    public int maxProfit(int[] prices) {
        int left = 0;
        int right = prices.length - 1;   
        int result = 0;
				
        while(left < right) {
            if(prices[left] < prices[right]) {
                if(result < prices[right] - prices[left]) {
                    result = prices[right] - prices[left]; 
                }
                right--;
            }
						
            if(prices[left] > prices[right]) {
                left++;
            }
					  if(prices[left] == prices[right]) {
						    left++;
					  }
        }
        return result;
    }
}
```


- 2차 제출 후, 틀리는 케이스 존재 [2,1,4]
```java
class Solution {
    public int maxProfit(int[] prices) {
        int left = 0;
        int right = prices.length - 1;   
        int result = 0;
				
        while(left < right) {
            if(prices[left] < prices[right]) {
                if(result < prices[right] - prices[left]) {
                    result = prices[right] - prices[left]; 
                }
								if(prices[left + 1] < prices[left] left ++;
								else right--;
            }
						
            if(prices[left] > prices[right]) {
                left++;
            }
					  if(prices[left] == prices[right]) {
						    left++;
					  }
        }
        return result;
    }
}
```

아예 접근을 달리해야 할 듯. 다음 포인터들의 계산을 보고 좌측을 움직일지 우측을 움직일지 정해야 함. 근데 좌측은 한번 가면 끝인데..

[right] - [left + 1]  랑 [right -1] - [left] 랑 더 나은 걸 하면 됨
7 10 5 3 6 4 라고 하면
4 - 10, 6 - 7

투포인터가 아니고 그냥 빼기를 다 계산해버리면 안되나
결국 최소 값은 찾아야 함.
최소 값의 인덱스를 찾으면, 그 다음 나머지 중에 최대 값을 찾으면 됨.

근데 또 무조건 최소 값이면 안되는 상황이긴 하네.

(여기서 포기하고 질문 했음)