---
layout: single
title: "CS 기술 면접 준비"
categories: algorithm
tags: [CS]
toc: true
author_profile: true
toc_sticky: true
toc_label: 목차
typora-root-url: ../
---

## 1. 자료구조 & 알고리즘

### 1.1 Array vs LinkedList
- Array
  - 메모리 구조: 연속된 메모리 블록에 순차적 저장
  - 시간 복잡도
    - 접근: O(1) - 인덱스로 직접 접근
    - 삽입/삭제: O(n) - 요소 이동 필요
  - 장점: 캐시 지역성, 빠른 접근
  - 단점: 크기 고정, 메모리 낭비 가능성
  - 사용 사례: 정렬된 데이터 검색, 빈번한 조회

- LinkedList
  - 메모리 구조: 포인터로 연결된 노드들
  - 시간 복잡도
    - 접근: O(n) - 순차적 탐색 필요
    - 삽입/삭제: O(1) - 포인터 변경만 필요
  - 장점: 동적 크기 조절, 효율적인 삽입/삭제
  - 단점: 추가 메모리 사용(포인터), 캐시 지역성 낮음
  - 사용 사례: 빈번한 삽입/삭제, 크기가 가변적인 데이터

### 1.2 Stack & Queue
- Stack
  - 구현 방법: 배열 또는 연결리스트
  - 주요 연산
    - push(): 요소 추가
    - pop(): 최상단 요소 제거
    - peek(): 최상단 요소 조회
  - 실제 활용
    - 함수 호출 관리
    - 괄호 매칭 검사
    - 웹 브라우저 방문 기록
    - DFS 구현

- Queue
  - 구현 방법: 원형 배열 또는 연결리스트
  - 주요 연산
    - enqueue(): 요소 추가
    - dequeue(): 첫 요소 제거
    - peek(): 첫 요소 조회
  - 실제 활용
    - BFS 구현
    - 프린터 대기열
    - 프로세스 스케줄링
    - 이벤트 처리

### 1.3 Hash Table
- 해시 함수
  - 좋은 해시 함수의 조건
    - 균등 분포
    - 계산 효율성
    - 일관성
  - 대표적인 해시 함수들
    - Division Method
    - Multiplication Method
    - Universal Hashing

- 충돌 해결 방법
  1. Chaining
     - 장점: 구현 간단, 적재율 제한 없음
     - 단점: 추가 메모리 필요
     - 구현: LinkedList 또는 Red-Black Tree 사용
  
  2. Open Addressing
     - Linear Probing
       - 장점: 캐시 효율성
       - 단점: 클러스터링
     - Quadratic Probing
       - 장점: 클러스터링 감소
       - 단점: 2차 클러스터링
     - Double Hashing
       - 장점: 클러스터링 최소화
       - 단점: 계산 비용

## 2. 운영체제

### 2.1 프로세스 vs 스레드
- 프로세스
  - 구성 요소
    - Code, Data, Stack, Heap
  - Context Switching 비용이 큼
  - IPC(Inter-Process Communication) 방법
    - 공유 메모리
    - 파이프
    - 소켓
    - 메시지 큐

- 스레드
  - 공유 자원
    - Code, Data, Heap
  - 개별 자원
    - Stack, Register
  - 동기화 이슈
    - Race Condition
    - Dead Lock
    - Critical Section

### 2.2 CPU 스케줄링
- 선점형 스케줄링
  1. Round Robin (RR)
     - 특징: 시간 할당량 기반
     - 장점: 응답 시간 예측 가능
     - 단점: 문맥 교환 오버헤드
  
  2. Priority Scheduling
     - 특징: 우선순위 기반
     - 문제점: 기아 현상
     - 해결책: Aging
  
  3. Multilevel Queue
     - 특징: 다중 큐 사용
     - 장점: 프로세스 특성별 처리
     - 단점: 큐 간 불균형

- 비선점형 스케줄링
  1. FCFS (First-Come, First-Served)
     - 특징: 도착 순서대로 처리
     - 문제점: Convoy Effect
  
  2. SJF (Shortest Job First)
     - 특징: 실행 시간 기준
     - 장점: 평균 대기 시간 최소화
     - 단점: 기아 현상

### 2.3 데드락(Deadlock)
- 발생 조건 (4가지 모두 만족해야 발생)
  1. 상호 배제 (Mutual Exclusion)
  2. 점유와 대기 (Hold and Wait)
  3. 비선점 (No Preemption)
  4. 순환 대기 (Circular Wait)

- 처리 방법
  1. 예방 (Prevention)
     - 4가지 조건 중 하나 제거
     - 장점: 데드락 완전 방지
     - 단점: 자원 활용률 저하
  
  2. 회피 (Avoidance)
     - Banker's Algorithm
     - 장점: 안전한 자원 할당
     - 단점: 미래 자원 요청 알아야 함
  
  3. 탐지 및 복구 (Detection & Recovery)
     - 자원 할당 그래프 사용
     - 복구 방법
       - 프로세스 종료
       - 자원 선점

## 3. 데이터베이스

### 3.1 트랜잭션
- ACID 특성
  1. Atomicity (원자성)
     - 구현: Undo/Redo 로그
  2. Consistency (일관성)
     - 구현: 무결성 제약 조건
  3. Isolation (격리성)
     - 구현: 락킹, MVCC
  4. Durability (지속성)
     - 구현: WAL(Write-Ahead Logging)

- 트랜잭션 격리 수준
  1. Read Uncommitted
     - 문제점: Dirty Read
  2. Read Committed
     - 문제점: Non-Repeatable Read
  3. Repeatable Read
     - 문제점: Phantom Read
  4. Serializable
     - 장점: 완벽한 격리
     - 단점: 성능 저하

### 3.2 인덱스
- B-Tree 인덱스
  - 구조: 루트, 브랜치, 리프 노드
  - 특징
    - 자동 밸런싱
    - 범위 검색 효율적
  - 적합한 상황
    - 범위 검색
    - 정렬이 필요한 경우

- Hash 인덱스
  - 구조: 해시 테이블
  - 특징
    - 정확한 일치 검색에 최적
    - 범위 검색 비효율
  - 적합한 상황
    - 메모리 기반 데이터베이스
    - 정확한 일치 검색

### 3.3 정규화
- 제1정규형 (1NF)
  - 원자값으로 구성
  - 반복 그룹 제거

- 제2정규형 (2NF)
  - 부분 함수적 종속 제거
  - 완전 함수적 종속 관계

- 제3정규형 (3NF)
  - 이행적 종속 제거
  - 결정자가 후보키가 아닌 함수적 종속 제거

- BCNF
  - 모든 결정자가 후보키
  - 가장 엄격한 정규형

## 4. 네트워크

### 4.1 TCP/IP
- TCP 3-way handshake
  1. SYN
  2. SYN + ACK
  3. ACK
  - 각 단계별 상태 변화
  - 실패 시나리오 처리

- TCP 흐름제어
  - Sliding Window
  - Stop and Wait
  - 혼잡 제어 알고리즘
    - Slow Start
    - Congestion Avoidance
    - Fast Recovery

### 4.2 HTTP
- HTTP 메서드
  - GET vs POST
  - PUT vs PATCH
  - 멱등성과 안전성

- REST 아키텍처
  1. Uniform Interface
  2. Stateless
  3. Cacheable
  4. Client-Server
  5. Layered System
  6. Code on Demand

- HTTP/2 특징
  - Multiplexing
  - Server Push
  - Header Compression
  - Binary Protocol

### 4.3 보안
- SSL/TLS 동작 과정
  1. 핸드셰이크
  2. 세션
  3. 종료

- 공개키 기반 구조 (PKI)
  - 인증서 체인
  - 인증서 검증
  - CRL과 OCSP

- 웹 보안
  - XSS 방어
  - CSRF 방어
  - SQL Injection 방어


