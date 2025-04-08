---
layout: single
title:  "[LeetCode] 리트코드 - Single Number (C++)"
categories: leetcode
tags: [리트코드, 비트연산, 해시테이블]
toc: true
author_profile: true
toc_sticky: true
toc_label: 목차
typora-root-url: ../
---

# [문제](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/549/)

**비어있지 않은** 정수배열 `nums`가 주어질 때, 하나를 제외한 모든 원소들이 두번씩 등장합니다.  
한번 등장하는 원소를 찾으세요.  
선형 시간복잡도와 상수의 추가 공간으로 구현하여야 합니다.


## 예제 입력 1
```
nums = [2,2,1]
```

## 예제 출력 1
```
1
```

## 예제 입력 2
```
nums = [4,1,2,1,2]
```

## 예제 출력 2
```
4
```

## 예제 입력 3
```
nums = [1]
```

## 예제 출력 3
```
1
```

# 풀이

## 문제 해결 방법

이 문제는 배열에서 한 번만 나타나는 숫자를 찾는 문제입니다. 주요 해결 방법은 다음과 같습니다:

1. **비트 연산을 이용한 해결 방법**:
   - **XOR** 연산의 성질을 활용 (a^a=0, a^0=a)
   - 모든 숫자를 XOR하면 짝수 번 나타나는 숫자는 0이 되고, 한 번만 나타나는 숫자만 남음

2. **해시 테이블을 이용한 해결 방법**:
   - 각 숫자의 등장 횟수를 카운트
   - 한 번만 등장하는 숫자를 찾음

비트 연산을 이용한 방법의 시간 복잡도는 **O(N)**이고, 공간 복잡도는 **O(1)**입니다.

## 코드

### 비트 연산을 이용한 풀이

```c++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;
        }
        return result;
    }
};
```

### 해시 테이블을 이용한 풀이

```c++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        unordered_map<int, int> count;
        
        // 각 숫자의 등장 횟수를 카운트
        for (int num : nums) {
            count[num]++;
        }
        
        // 한 번만 등장하는 숫자를 찾음
        for (const auto& pair : count) {
            if (pair.second == 1) {
                return pair.first;
            }
        }
        
        return 0; // 문제 조건상 항상 답이 존재하므로 이 부분은 실행되지 않음
    }
};
```

## 설명

### 비트 연산 풀이 설명

XOR 연산의 성질을 활용하여 문제를 해결합니다:

1. XOR 연산의 성질:
   - a^a = 0 (같은 숫자를 XOR하면 0)
   - a^0 = a (0과 XOR하면 자기 자신)
   - a^b^a = b (교환 법칙과 결합 법칙이 성립)

2. 모든 숫자를 XOR하면:
   - 짝수 번 나타나는 숫자는 0이 됨 (a^a = 0)
   - 한 번만 나타나는 숫자만 남음 (a^0 = a)

따라서 모든 숫자를 XOR한 결과가 한 번만 나타나는 숫자가 됩니다.

### 해시 테이블 풀이 설명

해시 테이블을 사용하여 각 숫자의 등장 횟수를 카운트합니다:

1. 각 숫자를 키로, 등장 횟수를 값으로 하는 해시 테이블을 생성
2. 모든 숫자를 순회하며 등장 횟수를 카운트
3. 해시 테이블을 순회하여 등장 횟수가 1인 숫자를 찾아 반환

이 방법은 시간 복잡도는 O(N)이지만, 공간 복잡도는 O(N)이므로 문제의 제약 조건을 만족하지 않습니다. 하지만 이해하기 쉽고 다른 유사한 문제에 적용하기 좋은 방법입니다.
