---
layout: single
title:  "[LeetCode] 리트코드 - Rotate Array (C++)"
categories: leetcode
tags: [리트코드, 배열, 역전]
toc: true
author_profile: true
toc_sticky: true
toc_label: 목차
typora-root-url: ../
---

# [문제](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/646/)

정수 배열 `nums`가 주어질 때, 배열을 오른쪽으로 `k`번 회전하세요.  
`k`는 음수가 아닌 정수입니다.

**주의사항:**
- 배열을 제자리에서 수정해야 합니다.
- O(1)의 추가 공간만 사용해야 합니다.

## 예제 입력 1
```
nums = [1,2,3,4,5,6,7], k = 3
```

## 예제 출력 1
```
[5,6,7,1,2,3,4]
```

## 예제 입력 2
```
nums = [-1,-100,3,99], k = 2
```

## 예제 출력 2
```
[3,99,-1,-100]
```

# 풀이

## 문제 해결 방법

이 문제는 배열을 오른쪽으로 k번 회전하는 문제입니다. 주요 해결 방법은 다음과 같습니다:

1. **역전(Reverse) 방법**:
   - 전체 배열을 역전
   - 처음 k개 원소를 역전
   - 나머지 원소를 역전

2. **순환 이동(Cyclic Replacements) 방법**:
   - 각 원소를 k칸 오른쪽으로 이동
   - 이동된 원소의 원래 위치에 있던 원소를 다음으로 이동
   - 모든 원소가 이동할 때까지 반복

역전 방법의 시간 복잡도는 **O(N)**이고, 공간 복잡도는 **O(1)**입니다.

## 코드

### 역전(Reverse) 방법을 이용한 풀이

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n; // k가 배열 길이보다 큰 경우 처리
        
        // 전체 배열 역전
        reverse(nums.begin(), nums.end());
        
        // 처음 k개 원소 역전
        reverse(nums.begin(), nums.begin() + k);
        
        // 나머지 원소 역전
        reverse(nums.begin() + k, nums.end());
    }
};
```

### 순환 이동(Cyclic Replacements) 방법을 이용한 풀이

```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n; // k가 배열 길이보다 큰 경우 처리
        
        int count = 0; // 이동된 원소의 개수
        
        for (int start = 0; count < n; start++) {
            int current = start;
            int prev = nums[start];
            
            do {
                int next = (current + k) % n;
                int temp = nums[next];
                nums[next] = prev;
                prev = temp;
                current = next;
                count++;
            } while (start != current);
        }
    }
};
```

## 설명

### 역전(Reverse) 방법 설명

역전 방법은 배열을 세 부분으로 나누어 역전하는 방식입니다:

1. 전체 배열을 역전합니다.
   - [1,2,3,4,5,6,7] → [7,6,5,4,3,2,1]

2. 처음 k개 원소를 역전합니다.
   - [7,6,5,4,3,2,1] → [5,6,7,4,3,2,1]

3. 나머지 원소를 역전합니다.
   - [5,6,7,4,3,2,1] → [5,6,7,1,2,3,4]

이 방법은 직관적이지 않지만, 수학적으로 정확한 결과를 제공합니다. 예를 들어, k=3인 경우:
- 전체 역전: [1,2,3,4,5,6,7] → [7,6,5,4,3,2,1]
- 처음 3개 역전: [7,6,5,4,3,2,1] → [5,6,7,4,3,2,1]
- 나머지 역전: [5,6,7,4,3,2,1] → [5,6,7,1,2,3,4]

### 순환 이동(Cyclic Replacements) 방법 설명

순환 이동 방법은 각 원소를 k칸 오른쪽으로 이동시키는 방식입니다:

1. 시작 위치에서 k칸 오른쪽으로 이동할 위치를 계산합니다.
2. 이동할 위치의 원소를 임시 변수에 저장합니다.
3. 현재 원소를 이동할 위치에 복사합니다.
4. 임시 변수에 저장한 원소를 다음 이동의 현재 원소로 사용합니다.
5. 모든 원소가 이동할 때까지 반복합니다.

이 방법은 각 원소가 정확히 한 번만 이동하므로 효율적입니다. 하지만 구현이 복잡할 수 있습니다.

### k가 배열 길이보다 큰 경우 처리

k가 배열 길이보다 큰 경우, k % n을 사용하여 실제 회전 횟수를 계산합니다. 예를 들어, 배열 길이가 7이고 k가 10인 경우, 실제로는 3번만 회전하면 됩니다.

