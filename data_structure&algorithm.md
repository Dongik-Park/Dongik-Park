# 자료구조(Data structure) 및 알고리즘(Algorithm)
## **자료구조** 
### 개념(Concept)

```
자료구조(data structure)는 전산학에서 자료를 효율적으로 이용할 수 있도록 컴퓨터에 저장하는 방법이다. 신중히 선택한 자료구조는 보다 효율적인 알고리즘을 사용할 수 있게 한다. 

In computer science, a data structure is a data organization, management and storage format that enables efficient access and modification.More precisely, a data structure is a collection of data values, the relationships among them, and the functions or operations that can be applied to the data.
```

> Refernece : [wiki : 자료구조](https://en.wikipedia.org/wiki/Data_structure)

```
                                                  +-------------------+
                                                  |   Data Structure  |
                                                  +-------------------+
                                                            |
                                   ---------------------------------------------------
                                   |                                                 |
                             +------------+                                   +------------+
                             |   Linear   |                                   | Non-Linear |
                             +------------+                                   +------------+
                                   |                                                 |
                ------------------------------------------                    ---------------
                |            |            |              |                    |             |
           +---------+  +---------+  +---------+  +-------------+         +--------+    +---------+
           |  List   |  |  Stack  |  |  Queue  |  | Linked List |         |  Tree  |    |  Graph  |
           +---------+  +---------+  +---------+  +-------------+         +--------+    +---------+  
```

### 선형 자료 구조(Linear)

> 선형구조란 자료를 구성하는 데이터를 순차적으로 나열시킨 형태를 의미한다.

* 리스트(List)
* 스택(Stack)
* 큐(Queue)
* 연결리스트(Linked List)

### 비선형 자료 구조(Non-Linear)

> 비선형구조란 하나의 자료 뒤에 여러개의 자료가 존재할 수 있는 것을 의미한다. 

* 트리(Tree)
* 그래프(Graph)

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

### 완전 검색 성능 비교(Brute force performance comparison) 
<hr>

알고리즘 문제를 해결하다보면 완전검색(Brute Force)를 이용하는 경우가 많다. 모든 경우의 수를 확인해야하는 경우에 대해 bit연산을 활용하여 모든 경우의 부분 집합을 만드는 방법과 재귀 호출(Recursive invocation)을 활용하는 방법 중 어떠한 방법이 효과적일까에 대해 고민하게 된다. 아래에 그에 대한 테스트 결과 코드를 작성하였다.

```java

import java.util.Random;

public class PowerSet3 {

	static int arr[] = {8,3,16,6,14,18,15,17,12,2,19,13,7,5,11,10,4,9,1,20}; // 1~24
	static int n = arr.length; // 24
	
	public static void dfs(int[]bit,int idx) {
		// exit condition
		if(idx == n) return;
		// include
		bit[idx] = 1;
		print(bit, idx);
		dfs(bit,idx + 1);
		// remove
		bit[idx] = 0;
		print(bit, idx);
		dfs(bit,idx + 1);
		return;
	}
	
	public static void loop(int[]bit, int N) {
		for(int i = 0; i < (1 << n); ++i) { // 1<<n : 부분집합의 개수 ( 1을 n번 shift하면 2^n )
			for(int j = 0; j < n; ++j) {
				if((i & 1 << j) == 1 << j)
					bit[j] = 1;
				else 
					bit[j] = 0;
			}
			print(bit, n);
		}
	}

	public static void main(String[] args) {
		int bit[] = new int[n];
		
		System.out.println("2^" + n + "(="+ (1<<n) +") cases test.\n");
		
		System.out.println("-----------loop start-----------");
		long start = System.currentTimeMillis(); // loop start point

		loop(bit,n);

		long end = System.currentTimeMillis(); // loop end point
		System.out.println( "For loop time : " + ( end - start )/1000.0 +"sec");
		System.out.println("------------loop end------------\n");

		System.out.println("---------Recursive start---------");
		start = System.currentTimeMillis(); // recursive start point

		dfs(bit,0);

		end = System.currentTimeMillis(); // recursive end point
		System.out.println( "Recursive time : " + ( end - start )/1000.0 +"sec");
		System.out.println("----------Recursive end----------\n");
	}

	public static void print(int[]bit, int n) {
		// No Execution
		/*for(int i = 0 ; i < n; ++i)
			if(bit[i] == 1)
				System.out.print(arr[i] + " ");
		*/
	}
}

```

24개(n)의 원소로 이루어진 배열의 완전검색(brute force)을 적용하여 프로그램을 실행시켰을 때, loop의 경우 각 케이스마다 경우의 수를 만들기 위해 n번의 loop를 돌아야하므로 2^24(=16777216) * 24(n) = 402,653,184(O(n2^n))번의 loop를 돌게된다. 재귀적(Recursive)으로 호출하였을 때에는 2^24 - 1(=16777215)번(O(2^n))의 재귀호출이 발생한다.

```cmd
2^24(=16777216) cases test.

-----------loop start-----------
For loop time : 0.879sec
------------loop end------------

---------Recursive start---------
Recursive time : 0.031sec
----------Recursive end----------
```
> 일반적으로 컴퓨터는 1초에 약 1억 번의 연산이 가능하다.

사실 당연한 결과이지만 n=2^24(=16777216)인 경우에 대해 평균적으로 재귀 호출이 약 28배의 빠른 결과를 도출했다. 재귀 호출은 위와 같은 문제의 경우에 단순한 반복문보다 간결하고 유연한 코드를 작성할 수 있다는 것을 확인하였다.

```java
for(int i = 0; i < 2; ++i) {
	bit[0] = i;
	for(int j = 0; j < 2; ++j) {
		bit[1] = j;
		for(int k = 0; k < 2; ++k) {
			bit[2] = k;
			for(int l = 0; l < 2; ++l) {
				bit[3] = l;
				print(bit, n);
			}
		}
	}
}
```
만약 n=4일 경우에 위와 같은 방식으로도 bit배열을 만들 수 있지만 이러한 코드는 for문의 개수가 n에 종속적이므로 n이 상수인 경우를 제외하면 구현이 불가능하다. (가능하다고 해도 n=24이면 24중 for문을 만들어야한다.) 

따라서, 완전검색(Brute force) 방식을 이용하여 코딩할 때에는 **재귀 호출(Recursive) > 반복문(loop)** 임을 확인할 수 있었다.
