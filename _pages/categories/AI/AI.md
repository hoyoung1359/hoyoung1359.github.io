---
title: "인공지능"
layout: single
permalink: /categories/ai/
author_profile: true
sidebar_main: true
---

{% assign categories_max = 0 %}
{% for category in site.categories %}
  {% if category[0] == "LLM" %}
    {% assign category_count = category[1].size %}
    {% assign categories_max = categories_max | plus: category_count %}
  {% endif %}
{% endfor %}

<div class="notice">
  <h4 style="font-size: 1.5em;">인공지능 (총 {{ categories_max }}개의 포스트)</h4>
  <p style="font-size: 1.1em;">LLM, Computer Vision,  ... </p>
</div>

<div class="grid__wrapper">
  <!-- LLM 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">💡</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/LLM" rel="permalink">LLM</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">Large Language Model</p>
        {% assign LLM_posts = site.categories.LLM %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ LLM_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>



</div> 