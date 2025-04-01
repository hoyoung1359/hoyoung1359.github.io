---
layout: single
title:  "[알고리즘 특강] 5. Binary Search"
categories: algorithm
tags: [SWEA, C++,  이분탐색]
toc: true
author_profile: true
toc_sticky: true
toc_label: 목차
---

## 1. 이분탐색의 정의와 필요성

### 1.1 이분탐색이란?
- **정의**: 정렬된 리스트에서 특정 값을 찾는 알고리즘
- **특징**: 
  - 찾고자 하는 범위 안에 있는 중앙값(midpoint value)을 찾고
  - 중앙값과 찾고자 하는 값(target value)을 비교해 나가는 방식
  - 중앙값이 찾고자 하는 값보다 작으면, 중앙값의 오른쪽 범위 대상으로 같은 과정을 반복
  - 중앙값이 찾고자 하는 값보다 크면, 중앙값의 왼쪽 범위 대상으로 같은 과정을 반복

## 2. 이분탐색 구현

### 2.1 C++ 구현
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

### 2.2 구현 시 주의사항
- 데이터가 정렬되어 있어야 한다는 전제 조건이 필요
- 탐색에 걸리는 시간복잡도는 O(log N)
- 중앙값을 구할 때, (left + right) / 2 대신에 left + ((right - left) / 2)를 사용
  - left와 right가 충분히 커서 left + right가 오버플로우가 발생하는 경우를 방지하기 위함

## 3. Lower bound

### 3.1 Lower bound란?
- **정의**: 목표보다 크거나 같은 값이 최초로 나오는 위치
- **예시**: 다음 배열에서 20과 50의 lower bound를 구하면
  - 20보다 크거나 같은 값이 최초로 나오는 위치는 1
  - 50보다 크거나 같은 값이 최초로 나오는 위치는 5

### 3.2 Lower bound 구현
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

## 4. Upper bound

### 4.1 Upper bound란?
- **정의**: 목표보다 큰 값이 최초로 나오는 위치
- **예시**: 다음 배열에서 20과 50의 upper bound를 구하면
  - 20보다 큰 값이 최초로 나오는 위치는 4
  - 50보다 큰 값이 최초로 나오는 위치는 5

### 4.2 Upper bound 구현
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

## 5. Parametric Search

### 5.1 Parametric Search란?
- **정의**: 최적화 문제를 결정 문제로 바꾸어 풀 수 있는 기법
- **특징**: 
  - 최적화 문제: f(x) = True가 되는 x의 최대값 구하기
  - 결정 문제: f(x) = True가 되는 어떤 x

### 5.2 Parametric Search 예시
n 개의 섬, m개의 다리가 있다. 다리마다 무게제한 (1<=무게<=10^9)이 있어 제한보다 무거운 차량이 지나가면 다리가 무너진다. 1번섬에서 n번섬으로 이동할 수 있는 차량 무게값의 최댓값을 얼마인가?

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

## 6. 이분탐색 구현 주의사항

### 6.1 주요 주의점
- 이분탐색을 구현할 때 장료 조건과, 구간을 쪼개는 과정에서 무한 루프를 조심해야 함
- left, right에서 +1, -1을 다른쪽에 하거나, mid 값을 구하는 방법을 바꾸면 무한루프가 되거나 한점을 탐색하지않고 건너뛸 수 있음
