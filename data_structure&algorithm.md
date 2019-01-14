# 자료구조(Data structure) 및 알고리즘(Algorithm)
## **자료구조** 
### 개념(Concept)

```
자료구조(data structure)는 전산학에서 자료를 효율적으로 이용할 수 있도록 컴퓨터에 저장하는 방법이다. 신중히 선택한 자료구조는 보다 효율적인 알고리즘을 사용할 수 있게 한다. 

In computer science, a data structure is a data organization, management and storage format that enables efficient access and modification.More precisely, a data structure is a collection of data values, the relationships among them, and the functions or operations that can be applied to the data.
```

> Refernece : [wiki : 자료구조](https://en.wikipedia.org/wiki/Data_structure)

### 선형 자료 구조(Linear)

> 선형구조란 자료를 구성하는 데이터를 순차적으로 나열시킨 형태를 의미한다.

### 비선형 자료 구조(Non-Linear)

> 비선형구조란 하나의 자료 뒤에 여러개의 자료가 존재할 수 있는 것을 의미한다. 

## **알고리즘**

### 알고리즘 설계기법

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
:----: | :----: | :----: | :----: | :----: | :----: | :----:
버블정렬 | O(n^2) | O(n^2) | 1 | 비교와 교환 | O | 코딩하기 쉽다
선택정렬 | O(n^2) | O(n^2) | 1 | 비교와 교환 | X | 교환 횟수가 버블, 삽입에 비해 적다
삽입정렬 | O(n^2) | O(n^2) | 1 | 비교와 교환 | O | n의 개수가 적을때 효과적이다
퀵정렬 | O(nlogn) | O(n^2) | logn ~ n | 분할정복 | X | 평균 속도가 가장 빠르다
병합정렬 | O(nlogn) | O(nlogn) | n | 비교와 교환 | O | 연결 리스트의 경우 가장 효과적인 방법
카운팅정렬 | O(n+k) | O(n+k) | n | 비교환 방식 | O | n이 비교적 작을 때만 가능하다
힙 정렬 | O(nlogn) | O(nlogn) | 1 | 분할정복 | X | 평균 계산 속도에서 퀵정렬 보다 느리다

> [**Comparison Sorting Algorithms**](https://www.toptal.com/developers/sorting-algorithms)

![**정렬 알고리즘 비교**](https://cdn-images-1.medium.com/max/1600/1*bPpvELo9_QqQsDz7CSbwXQ.gif)

### DFS(Depth First Search)
// TODO
재귀, 반복 (부분집합 생성하기)
재귀와 bit연산을 이용한 것의 시간차이 계산

```java
public class Z08_PowerSet2 {

	static int arr[] = {3,6,7,1,5,4};
	
	public static void main(String[] args) {
		
		int n = arr.length;
		
		int bit[] = new int[n];
		
		int cnt = 0;
		
		for(int i = 0; i < (1 << n); ++i) { // 1<<n : 부분집합의 개수 ( 1을 n번 shift하면 2^n )
			for(int j = 0; j < n; ++j) {
				if((i & 1 << j) == 1 << j)
					bit[j] = 1;
				else 
					bit[j] = 0;
			}
			
			print(bit, cnt++);
		}
	}

	public static void print(int[]bit, int cnt) {
		System.out.print(cnt + "번 : ");
		for(int i = 0 ; i < bit.length; ++i)
			if(bit[i] == 1)
				System.out.print(arr[i] + ",");
		System.out.println();
	}

}
```
