# 파이썬 heapq 모듈 정리

파이썬은 heapq를 지원해주기 때문에 힙 알고리즘이 필요할 때 유용하게 사용할 수 있다!

파이썬 정말 좋아…

```python
import heapq

heapq.heapify(x) # 리스트 x를 힙으로 변환

heapq.heappush(heap, item) # 푸시
heapq.heappop(heap) # heap에서 가장 작은 항목을 pop하고 return
heap[0] # pop하지 않고 가장 작은 항목에 접근

heapq.heappushpop(heap, item) # heap에 item을 push한 다음, heap에서 가장 작은 항목을 pop하고 return
heapq.heapreplace(heap, item) # 힙에서 가장 작은 항목을 pop하고 return하며, 새로운 item을 push함

heapq.merge(*iterables, key=None, reverse=False) # 여러 정렬된 입력을 단일 정렬된 출력으로 병합

heapq.nlargest(n, iterable, key=None) # iterable에 의해 정의된 데이터 집합에서 n 개의 가장 큰 요소로 구성된 리스트를 반환
heapq.nsmallest(n, iterable, key=None) # iterable에 의해 정의된 데이터 집합에서 n 개의 가장 작은 요소로 구성된 리스트를 반환
```
---
출처
[파이썬 공식 문서](https://docs.python.org/ko/3/library/heapq.html)
