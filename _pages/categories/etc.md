---
title: "기타"
layout: single
permalink: /categories/etc/
author_profile: true
sidebar_main: true
---

{% assign categories_max = 0 %}
{% for category in site.categories %}
  {% if category[0] == "blog" or category[0] == "video-editing" or category[0] == "english" or category[0] == "mac" %}
    {% assign category_count = category[1].size %}
    {% assign categories_max = categories_max | plus: category_count %}
  {% endif %}
{% endfor %}

<div class="notice">
  <h4>기타 카테고리 (총 {{ categories_max }}개의 포스트)</h4>
  <p>기타 다양한 주제의 포스트들을 모아놓은 카테고리입니다.</p>
</div>

<div class="grid__wrapper">
  <!-- 블로그 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">📝</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/blog" rel="permalink">블로그</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">블로그 관련 포스트</p>
        {% assign blog_posts = site.categories.blog %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ blog_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <!-- 영상편집 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">🎬</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/video-editing" rel="permalink">영상편집</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">영상편집 관련 포스트</p>
        {% assign video_posts = site.categories.video-editing %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ video_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <!-- 영어단어 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">📚</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/english" rel="permalink">영어단어</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">영어 학습 관련 포스트</p>
        {% assign english_posts = site.categories.english %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ english_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>

  <!-- Mac 카테고리 -->
  <div class="grid__item" style="padding: 2em; text-align: center; border: 1px solid #f2f3f3; border-radius: 4px; margin-bottom: 1em; background: white;">
    <div style="font-size: 2em; margin-bottom: 0.5em;">🍎</div>
    <div class="archive__item">
      <h2 class="archive__item-title no_toc" itemprop="headline" style="margin: 0 0 10px 0; padding-bottom: 0.3em;">
        <a href="/categories/mac" rel="permalink">Mac</a>
      </h2>
      <div class="archive__item-excerpt" style="margin-top: 0.5em; font-size: 0.9em; line-height: 1.5;">
        <p style="margin: 0;">Mac 단축키 및 꿀팁 모음</p>
        {% assign mac_posts = site.categories.mac %}
        <p style="margin: 0.5em 0 0 0; color: #666;">{{ mac_posts.size }}개의 포스트</p>
      </div>
    </div>
  </div>
</div> 