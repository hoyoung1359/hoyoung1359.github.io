---
layout: single
title:  "[알고리즘 특강] 5. Binary Search"
categories: algorithm
tags: [SWEA, C++, Binary Search]
toc: true
author_profile: true
---


이분탐색 (Binary Search)  

정렬된 리스트에서 특정 값을 찾는 알고리즘   
찾고자 하는 범위 안에 있는 중앙값(midpoint value)를 찾고,   
중앙값과 찾고자 하는 값(target value)을 비교해 나가는 방식  

중앙값이 찾고자 하는 값보다 작으면, 중앙값의 오른쪽 범위 대상으로 같은 과정을 반복한다.
중앙값이 찾고자 하는 값보다 크면, 중앙값의 왼쪽 범위 대상으로 같은 과정을 반복한다.  

# 이분 탐색 구현

C++ 에서 이분탐색 구현  

데이터가 정렬되어 있어야 한다는 전제 조건이 필요하다.  
탐색 범위를 반으로 줄여나가기 때문에 탐색에 걸리는 시간복잡도는 O(log N) 만큼의 시간이 소요된다.
중앙값을 구할 때, (left + right) / 2 대신에  
left + ( (right - left) / 2 ) 를 쓴 이유:  
left와 right가 충분히 커서  
left + right가 오버플로우가 발생하는 경우를 방지하기 위함   

```c++
#define MAX_N 100

int main() {
    int N;			// 데이터의 전체 크기
    int arr[MAX_N]	// 데이터를 담은 배열
    int target; 	// 찾고자 하는 값
    
    // 범위 구간 설정
    
}
```

# lower bound

이분탐색을 이용해 lower bound를 구현할 수 있다.
lower bound: 목표보다 크거나 같은 값이 최초로 나오는 위치  

예시  
다음 배열에서 20과 50의 lower bound를 구하면,
20보다 크거나 같은 값이 최초로 나오는 위치는 1이고,   
50보다 크거나 같은 값이 최초로 나오는 위치는 5이다



# lower bound 구현

C++ 에서 lower blund를 구현

아이디어  
다음 배열에서 20의 lower bound를 구한다고 해보자.
20보다 크거나 같은 원소들을 True로 표시해보면, 결국 첫번째 True가 나오는 위치를 찾는 것이다.  

True인 곳보다 오른쪽은 항상 True가 나오고,
True인 곳보다 왼쪽은 True가 나올 가능성이 있다.  
또한, False인 곳보다 오른쪽은 True가 나올 가능성이 있다.  

즉, 중앙값이 True가 나온다면, 왼쪽에서 True가 나올 가능성이 있으므로 왼쪽 범위를 탐색하고, 중앙값이 False가 나온다면, 오른쪽에서 True가 나올 가능성이 있으므로 오른쪽 범위를 탐색한다.  

```c++
#define MAX_N 100

int main() {
    
}
```



# upper bound

이분 탐색을 이용해 upper bound를 구현할 수 있다.  
upper bound: 목표보다 크거나 같은 값이 최초로 나오는 위치

예시  
다음 배열에서 20과 50의 upper bound를 구하면,
20보다 큰 값이 최초로 나오는 위치는 4이고,   
50보다 큰 값이 최초로 나오는 위치는 5이다

# upper bound 구현

C++ 에서 lower blund를 구현

아이디어  
다음 배열에서 20의 upper bound를 구한다고 해보자
20보다 큰 원소들을 True로 표시해보면,

중앙값이 True가 나온다면, 왼쪽에서 True가 나올 가능성이 있으므로 왼쪽 범위를 탐색하고, 중앙값이 False가 나온다면, 오른쪽에서 True가 나올 가능성이 있으므로 오른쪽 범위를 탐색한다.    

lower bound와의 차이는 조건에 차이가 있을 뿐, 나머지 로직은 동일하다.  

```c++
#define MAX_N 100

int main() {
    
}
```

# Parametric Search

단순히 정렬된 배열 안에서 원소를 찾는 이분 탐색을 응용하여 최적화 문제를 결정 문제로 바꾸어 풀 수 있음.

