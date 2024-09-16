---
layout: single
title:  "특강 3. Union Find"
categories: algorithm
tags: [SWEA, C++, UNIONFIND]
toc: true
author_profile: true
---

Union-Find

Union-Find는 상호 배타적 집합(서로소 집합)(Disjoint-Set) 을 표현할 때 사용하는 그래프 알고리즘이다.
임의의 두 노드(원소)가 서로 같은 그래프(집합)에 속하는지 판별하는 알고리즘(집합을 트리 구조를 이용하여 구현)
Disjoint-Set이란?
공통원소가 없는 "상호 배타적인" 부분집합들로 나눠진 원소들에 대한 정보를 표현하는 자료구조이다.
지합을 합치는 Union연산과 노드의 루트 노드를 찾는 Find연산으로 이루어진다.
Union (합치기): 두 원소가 속한 집합을 하나로 합친다.
Find(찾기): 해당 원소가 속한 집합을 반환한다.
