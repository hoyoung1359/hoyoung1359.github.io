---
layout: single
title:  "[LeetCode] 리트코드 - Intersection of Two Arrays II (C++)"
categories: leetcode
tags: [리트코드, 해시테이블, 정렬, 이진탐색]
toc: true
author_profile: true
toc_sticky: true
toc_label: 목차
typora-root-url: ../
---

# [문제](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/674/)

두 개의 정수 배열 `nums1`과 `nums2`가 주어질 때, 두 배열의 교집합을 반환하세요.  
결과에 나타나는 각 원소의 횟수는 두 배열에서 나타나는 횟수의 최소값과 같아야 합니다.  
결과는 임의의 순서로 반환할 수 있습니다.

## 예제 입력 1
```
nums1 = [1,2,2,1], nums2 = [2,2]
```

## 예제 출력 1
```
[2,2]
```

## 예제 입력 2
```
nums1 = [4,9,5], nums2 = [9,4,9,8,4]
```

## 예제 출력 2
```
[4,9]
```
또는
```
[9,4]
```

# 풀이

## 문제 해결 방법

이 문제는 두 배열의 교집합을 찾는 문제입니다. 주요 해결 방법은 다음과 같습니다:

1. **해시 테이블을 이용한 해결 방법**:
   - 첫 번째 배열의 각 원소와 등장 횟수를 해시 테이블에 저장
   - 두 번째 배열을 순회하며 해시 테이블에 있는 원소를 결과에 추가

2. **정렬 후 이진 탐색을 이용한 해결 방법**:
   - 두 배열을 정렬
   - 첫 번째 배열의 각 원소에 대해 두 번째 배열에서 이진 탐색으로 찾기

3. **정렬 후 투 포인터를 이용한 해결 방법**:
   - 두 배열을 정렬
   - 두 포인터를 사용하여 공통 원소 찾기

해시 테이블 방법의 시간 복잡도는 **O(N+M)**이고, 공간 복잡도는 **O(min(N,M))**입니다.

## 코드

### 해시 테이블을 이용한 풀이

```c++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        // nums1이 더 작은 배열이 되도록 스왑
        if (nums1.size() > nums2.size()) {
            return intersect(nums2, nums1);
        }
        
        // nums1의 각 원소와 등장 횟수를 해시 테이블에 저장
        unordered_map<int, int> count;
        for (int num : nums1) {
            count[num]++;
        }
        
        vector<int> result;
        // nums2를 순회하며 해시 테이블에 있는 원소를 결과에 추가
        for (int num : nums2) {
            if (count[num] > 0) {
                result.push_back(num);
                count[num]--;
            }
        }
        
        return result;
    }
};
```

### 정렬 후 이진 탐색을 이용한 풀이

```c++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        // 두 배열 정렬
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());
        
        vector<int> result;
        vector<bool> used(nums2.size(), false);
        
        // nums1의 각 원소에 대해 이진 탐색으로 nums2에서 찾기
        for (int num : nums1) {
            int left = 0, right = nums2.size() - 1;
            
            while (left <= right) {
                int mid = left + (right - left) / 2;
                
                if (nums2[mid] == num && !used[mid]) {
                    result.push_back(num);
                    used[mid] = true;
                    break;
                } else if (nums2[mid] < num) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }
        
        return result;
    }
};
```

### 정렬 후 투 포인터를 이용한 풀이

```c++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        // 두 배열 정렬
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());
        
        vector<int> result;
        int i = 0, j = 0;
        
        // 투 포인터를 사용하여 공통 원소 찾기
        while (i < nums1.size() && j < nums2.size()) {
            if (nums1[i] < nums2[j]) {
                i++;
            } else if (nums1[i] > nums2[j]) {
                j++;
            } else {
                result.push_back(nums1[i]);
                i++;
                j++;
            }
        }
        
        return result;
    }
};
```

## 설명

### 해시 테이블 풀이 설명

해시 테이블을 사용하여 첫 번째 배열의 각 원소와 등장 횟수를 저장한 후, 두 번째 배열을 순회하며 공통 원소를 찾습니다:

1. 첫 번째 배열의 각 원소와 등장 횟수를 해시 테이블에 저장합니다.
2. 두 번째 배열을 순회하며 해시 테이블에 있는 원소를 결과에 추가합니다.
3. 원소가 추가될 때마다 해시 테이블의 등장 횟수를 감소시킵니다.

이 방법은 시간 복잡도가 O(N+M)이고, 공간 복잡도는 O(min(N,M))입니다. 첫 번째 배열이 더 작은 배열이 되도록 스왑하여 공간 복잡도를 최적화합니다.

### 정렬 후 이진 탐색 풀이 설명

두 배열을 정렬한 후, 첫 번째 배열의 각 원소에 대해 두 번째 배열에서 이진 탐색으로 찾는 방법입니다:

1. 두 배열을 정렬합니다.
2. 첫 번째 배열의 각 원소에 대해 두 번째 배열에서 이진 탐색으로 찾습니다.
3. 찾은 원소가 이미 사용되었는지 확인하고, 사용되지 않았다면 결과에 추가합니다.

이 방법은 시간 복잡도가 O(N log M)이고, 공간 복잡도는 O(1)입니다. 하지만 이진 탐색은 중복된 원소를 찾기 어려울 수 있어, 추가적인 처리가 필요합니다.

### 정렬 후 투 포인터 풀이 설명

두 배열을 정렬한 후, 두 포인터를 사용하여 공통 원소를 찾는 방법입니다:

1. 두 배열을 정렬합니다.
2. 두 포인터를 사용하여 공통 원소를 찾습니다.
3. 두 원소가 같으면 결과에 추가하고 두 포인터를 모두 증가시킵니다.
4. 두 원소가 다르면 작은 원소의 포인터를 증가시킵니다.

이 방법은 시간 복잡도가 O(N log N + M log M)이고, 공간 복잡도는 O(1)입니다. 정렬이 필요하지만, 투 포인터를 사용하여 효율적으로 공통 원소를 찾을 수 있습니다.

