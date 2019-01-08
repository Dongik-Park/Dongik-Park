# 알고리즘(Algorithm)
## 알고리즘 설계기법

1. 완전검색(Brute Force) : 
    * 장점 : 반드시 답을 찾을 수 있다.
    * 단점 : 시간이 제일 오래 걸린다. 

2. 가지치기(Backtracking) :
    * 장점 : 답을 찾으면 탐색을 종료한다.
    * 단점 : 스택 오버플로우와 같은 성능 이슈 (Stack overflow issue)

3. 분할정복(Divide & Conquer) :
    * 장점 : 문제를 나눔으로써(병렬적으로) 어려운 문제를 해결해 나갈 수 있다.
    * 단점 : 정렬이 되어있어야 한다는 전제가 필요하다는 점과 재귀호출 사용 시 발생하는 문제가 존재한다.
    
4. 탐욕기법(Greedy) :
    * 장점 : 현재 위치에서 최적의 선택을 해나간다. 
    * 단점 : 최적의 선택(가설)에 대한 증명을 요구한다. (Require Local optimization -> Global optimization)

5. 동적계획법(Dynamic Programming) :
    * 장점 : 필요한 모든 가능성을 고려하므로 항상 최적의 결과를 도출할 수 있다.
    * 단점 : 모든 가능성을 고려하지 하지 못할 경우 최적의 결과를 보장할 수 없으며, 다른 방법론에 비해 상대적으로 많은 메모리를 요구한다.

> **알고리즘 시각화 참고(Algorithm visualization reference)** : [VisuAlgo](https://visualgo.net/ko)

### 정렬 알고리즘

명칭 | 평균 수행시간 | 최악 수행시간 | 보조메모리 | 알고리즘 기법 | 안정성 | 비고
---- | ---- | ---- | ---- | ---- |---- | ----
버블정렬 | O(n^2) | O(n^2) | 1 | 비교와 교환 | O | 코딩하기 쉽다
선택정렬 | O(n^2) | O(n^2) | 1 | 비교와 교환 | X | 교환 횟수가 버블, 삽입에 비해 적다
삽입정렬 | O(n^2) | O(n^2) | 1 | 비교와 교환 | O | n의 개수가 적을때 효과적이다
퀵정렬 | O(nlogn) | O(n^2) | logn ~ n | 분할정복 | X | 평균 속도가 가장 빠르다
병합정렬 | O(nlogn) | O(nlogn) | n | 비교와 교환 | O | 연결 리스트의 경우 가장 효과적인 방법
카운팅정렬 | O(n+k) | O(n+k) | n | 비교환 방식 | O | n이 비교적 작을 때만 가능하다
힙 정렬 | O(nlogn) | O(nlogn) | 1 | 분할정복 | X | 평균 계산 속도에서 퀵정렬 보다 느리다

> [**Comparison Sorting Algorithms**](https://www.toptal.com/developers/sorting-algorithms)

![**정렬 알고리즘 비교**](https://cdn-images-1.medium.com/max/1600/1*bPpvELo9_QqQsDz7CSbwXQ.gif)