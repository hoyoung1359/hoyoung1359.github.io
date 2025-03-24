---
layout: single
title:  "[알고리즘 특강] 5. Binary Search"
categories: algorithm
tags: [SWEA, C++,  이분탐색]
toc: true
author_profile: true
---

# 이분탐색 (Binary Search)  

정렬된 리스트에서 특정 값을 찾는 알고리즘   
찾고자 하는 범위 안에 있는 중앙값(midpoint value)를 찾고,   
중앙값과 찾고자 하는 값(target value)을 비교해 나가는 방식  

중앙값이 찾고자 하는 값보다 작으면, 중앙값의 오른쪽 범위 대상으로 같은 과정을 반복한다.
중앙값이 찾고자 하는 값보다 크면, 중앙값의 왼쪽 범위 대상으로 같은 과정을 반복한다.  

# 이분 탐색 구현

- C++ 에서 이분탐색 구현  

- 데이터가 정렬되어 있어야 한다는 전제 조건이 필요하다.  
	탐색 범위를 반으로 줄여나가기 때문에 탐색에 걸리는 시간복잡도는 O(log N) 만큼의 시간이 소요된다.
- 중앙값을 구할 때, (left + right) / 2 대신에  
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
    int left = 0;
    int right = N-1;
    
    while (left <= right) {
        // left~right 구간의 중간값 구하기
        int mid = left + ((right-left) / 2);
        
        // 목표를 찾았을 경우
        if (arr[mid] == target){
            // 원하는 작업 수행
        }
        
        // 중앙값이 목표보다 작을 경우
        else if (arr[mid] < target) {
            // 중앙값 오른쪽 범위 탐색
            left = mid + 1;
        }
        
        // 중앙값이 목표보다 큰 경우
        else {
            // 중앙값 왼쪽 범위 탐색
            right = mid - 1;
        }
    }
}
```

# Lower bound

이분탐색을 이용해 lower bound를 구현할 수 있다.  
**lower bound:** 목표보다 크거나 같은 값이 최초로 나오는 위치  

예시  
다음 배열에서 20과 50의 lower bound를 구하면,
20보다 크거나 같은 값이 최초로 나오는 위치는 1이고, 50보다 크거나 같은 값이 최초로 나오는 위치는 5이다



# Lower bound 구현

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
    int N;	// 데이터의 전체 크기
    int arr[MAX_N]; // 데이터를 담은 배열 (오름차순정렬)
    int target;		//찾고자 하는 값
    
    // 범위 구간 설정
    int left = 0;
    int right = N-1;
    int ans = -1;
    
    while (left <= right) {
        // left~right 구간의 중간값 구하기
        int mid = left + ((right-left) / 2);

        // 중앙값이 목표보다 크거나 같을 경우
        if (arr[mid] >= target) {
            // 중앙값 왼쪽 범위 탐색
            right = mid - 1;
            ans = mid;
        }
        
        // 중앙값이 목표보다 작을 경우
        else {
            // 중앙값 오른쪽 범위 탐색
            left = mid + 1;
        }
    }
}
```



# Upper bound

이분 탐색을 이용해 upper bound를 구현할 수 있다.  
upper bound: 목표보다 크거나 같은 값이 최초로 나오는 위치

예시  
다음 배열에서 20과 50의 upper bound를 구하면,
20보다 큰 값이 최초로 나오는 위치는 4이고,   
50보다 큰 값이 최초로 나오는 위치는 5이다

# Upper bound 구현

C++ 에서 lower blund를 구현

아이디어  
다음 배열에서 20의 upper bound를 구한다고 해보자
20보다 큰 원소들을 True로 표시해보면,

중앙값이 True가 나온다면, 왼쪽에서 True가 나올 가능성이 있으므로 왼쪽 범위를 탐색하고, 중앙값이 False가 나온다면, 오른쪽에서 True가 나올 가능성이 있으므로 오른쪽 범위를 탐색한다.    

lower bound와의 차이는 조건에 차이가 있을 뿐, 나머지 로직은 동일하다.  

```c++
#define MAX_N 100

int main() {
    int N;	// 데이터의 전체 크기
    int arr[MAX_N]; // 데이터를 담은 배열 (오름차순정렬)
    int target;		//찾고자 하는 값
    
    // 범위 구간 설정
    int left = 0;
    int right = N-1;
    int ans = -1;
    
    while (left <= right) {
        // left~right 구간의 중간값 구하기
        int mid = left + ((right-left) / 2);

        // 중앙값이 목표보다 큰 경우
        if (arr[mid] > target) {
            // 중앙값 왼쪽 범위 탐색
            right = mid - 1;
            ans = mid;
        }
        
        // 중앙값이 목표보다 작을 경우
        else {
            // 중앙값 오른쪽 범위 탐색
            left = mid + 1;
        }
    }
}
```

# Parametric Search

단순히 정렬된 배열 안에서 원소를 찾는 이분 탐색을 응용하여 최적화 문제를 결정 문제로 바꾸어 풀 수 있음.  

최적화 문제: f(x) = True가 되는 x의 최대값 구하기  
결정 문제: f(x) = True가 되는 어떤 x  

가능한 모든 x값마다 f(x)가 True인지 검사하여 True중에서 최소/최대값을 고르면 최적화 문제를 결정 문제로 풀 수 있다.  
x1 < x2 이고 f(x1) = True 면, f(x2) = True 또는 f(x2) = True 면 f(x1) = True 라는 조건을 만족.
f(x)의 결과값이 정렬된 형태이기 때문에 이분탐색 아이디어를 적용하여 문제를 풀 수 있다.   

# Parametric Search 예시

n 개의 섬, m개의 다리가 있다. 다리마다 무게제한 (1<=무게<=10^9)이 있어 제한보다 무거운 차량이 지나가면 다리가 무너진다. 1번섬에서 n번섬으로 이동할 수 있는 차량 무게값의 최댓값을 얼마인가?  
-> Prim, Union-Find, Parametric Search등으로 풀 수 있음.  

만약 무게가 i 인 차량이 1번 섬에서 n번 섬으로 이동할 수 있다면, 그 길을 따라 i 보다 가벼운 차량도 이동 가능. 
만약 무게가 i 인 차량이 1번 섬에서 n번 섬으로 이동할 수 있다면, x보다 무거운 차량도 이동할수 없다.

| i    | 1    | -    | x    | x+1   | -    | 10^9  |
| ---- | ---- | ---- | ---- | ----- | ---- | ----- |
| f(i) | True | -    | True | False | -    | False |

1보다 가벼운 차량, 1-^보다 무거운 차량의 이동여부는 조사할 필요 없다.  
탐색 범위를 1~10^9 로 두고 이분탐색을 하면 된다.  

```c++
constexpr int MIN = 1;
constexpr int MAX = 1e9;

//  무게가 w인 차량이 1->n 섬 이동 가능 여부 리턴
bool f(int w){
	//...
}

// 1->n 번섬으로 이동 가능한 차량 무게의 최대값 리턴
int solve() {
	int left = MIN;
	int right = MAX;
	int ans = -1;
	
	while (left <= right) {
        // left~right 구간의 중간값 구하기
        int mid = left + ((right-left) / 2);

        // 무게가 mid인차량이 1->n 이동 가능
        if (f(mid)) {
            // 무게 늘리기
            left = mid + 1;
            ans = mid;
        }
        
        // 무게가 mid인차량이 1->n 이동 불가능
        else {
            // 무게 줄이기
            right = mid - 1;
        }
    }
    return ans;
}
```

# 이분 탐색 구현 주의사항

이분 탐색을 구현할 때 장료 조건과, 구간을 쪼개는 과정에서 무한 루프를 조심해야 한다  
left, right 에서 +1, -1을 다른쪽에 하거나, mid 값을 구하는 방법을 바꾸면 무한루프가 되거나 한점을 탐색하지않고 건너 뛸 수 있다.
