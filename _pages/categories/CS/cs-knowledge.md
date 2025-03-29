---
title: "CS 지식"
layout: single
permalink: /categories/cs-knowledge/
author_profile: true
sidebar_main: true
---

{% assign categories_max = 0 %}
{% for category in site.categories %}
  {% if category[0] == "algorithm" or category[0] == "datastructure" %}
    {% assign category_count = category[1].size %}
    {% assign categories_max = categories_max | plus: category_count %}
  {% endif %}
{% endfor %}

<div class="notice">
  <h4>CS 지식 카테고리 (총 {{ categories_max }}개의 포스트)</h4>
  <p>컴퓨터 과학 관련 지식들을 정리한 카테고리입니다.</p>
</div>

<div class="grid__wrapper">
  <!-- 알고리즘 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">💡</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/algorithm" rel="permalink">알고리즘</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">알고리즘 이론 및 문제 풀이</p>
        {% assign algorithm_posts = site.categories.algorithm %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ algorithm_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <!-- 운영체제 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">💻</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/OS" rel="permalink">운영체제</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">운영체제 개념정리</p>
        {% assign OS_posts = site.categories.OS %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ OS_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <!-- 네트워크 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">🌐</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/network" rel="permalink">네트워크</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">네트워크 개념정리</p>
        {% assign network_posts = site.categories.network %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ network_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <!-- DB 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">📚</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/DB" rel="permalink">데이터베이스</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">DB개념 및 예제</p>
        {% assign DB_posts = site.categories.DB %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ DB_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>



  <!-- 자료구조 카테고리 -->
  <!-- <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">📚</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/datastructure" rel="permalink">자료구조</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">자료구조 이론 및 구현</p>
        {% assign datastructure_posts = site.categories.datastructure %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ datastructure_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div> -->



</div> 