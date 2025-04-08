---
title: "문제풀이"
layout: single
permalink: /categories/problem-solving/
author_profile: true
sidebar_main: true
---

{% assign categories_max = 0 %}
{% for category in site.categories %}
  {% if category[0] == "baekjoon" %}
    {% assign category_count = category[1].size %}
    {% assign categories_max = categories_max | plus: category_count %}
  {% endif %}
{% endfor %}

<div class="notice">
  <h4>문제풀이 카테고리 (총 {{ categories_max }}개의 포스트)</h4>
  <p>알고리즘 문제 풀이를 정리한 카테고리입니다.</p>
</div>

<div class="grid__wrapper">
  <!-- 백준 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">⚡</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/baekjoon" rel="permalink">백준</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">백준 알고리즘 문제 풀이</p>
        {% assign baekjoon_posts = site.categories.baekjoon %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ baekjoon_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">⚡</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/leetcode" rel="permalink">리트코드</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">리트코드 문제 풀이</p>
        {% assign leetcode_posts = site.categories.leetcode %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ leetcode_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>



</div> 