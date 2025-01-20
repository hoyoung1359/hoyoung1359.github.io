---
layout: single # 원하는 레이아웃, 예: single, splash 
title: ""
permalink: /
author_profile: true
sidebar_main: true
classes: wide
---

<div style="background: linear-gradient(145deg, #fff4e6, #ffe8cc); padding: 25px; border-radius: 15px; margin: 30px auto; max-width: 800px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
  <h3 style="color: #ff6b6b; margin-bottom: 20px; text-align: center; font-size: 2.2em; font-weight: bold;">⚠️ WARNING ⚠️</h3>
  <div style="display: flex; flex-direction: column; gap: 15px;">
    <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); display: flex; align-items: center;">
      <span style="font-size: 2em; margin-right: 20px;">🤔</span>
      <p style="margin: 0; color: #4a4a4a; font-size: 1.1em;"><strong>1.</strong> 별거 아닌 거에 "어?" 금지</p>
    </div>
    <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); display: flex; align-items: center;">
      <span style="font-size: 2em; margin-right: 20px;">👥</span>
      <p style="margin: 0; color: #4a4a4a; font-size: 1.1em;"><strong>2.</strong> 한 사람 뒤에 세 명 이상 서있기 금지</p>
    </div>
    <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); display: flex; align-items: center;">
      <span style="font-size: 2em; margin-right: 20px;">🤫</span>
      <p style="margin: 0; color: #4a4a4a; font-size: 1.1em;"><strong>3.</strong> 모니터 쳐다보며 웅성웅성 금지</p>
    </div>
  </div>
</div>

<div class="grid__wrapper" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 30px; margin: 50px auto; max-width: 1200px; padding: 0 20px;">
  <div class="feature__item" style="text-align: center; padding: 30px; border-radius: 15px; background: linear-gradient(145deg, #ffffff, #f0f0f0); box-shadow: 5px 5px 15px #d1d1d1, -5px -5px 15px #ffffff; min-width: 280px;">
    <span style="font-size: 3.5em; margin-bottom: 15px; display: block;">🎮</span>
    <h2 style="font-size: 1.5em; margin: 15px 0;">게임 개발</h2>
    <p style="margin: 15px 0; line-height: 1.6;">유니티와 언리얼로 만드는<br>게임 개발 이야기</p>
    <a href="/categories/game" class="btn btn--primary" style="display: inline-block; padding: 10px 25px; margin-top: 10px; border-radius: 25px;">더보기</a>
  </div>
  
  <div class="feature__item" style="text-align: center; padding: 30px; border-radius: 15px; background: linear-gradient(145deg, #ffffff, #f0f0f0); box-shadow: 5px 5px 15px #d1d1d1, -5px -5px 15px #ffffff; min-width: 280px;">
    <span style="font-size: 3.5em; margin-bottom: 15px; display: block;">💻</span>
    <h2 style="font-size: 1.5em; margin: 15px 0;">웹 개발</h2>
    <p style="margin: 15px 0; line-height: 1.6;">프론트엔드부터 백엔드까지<br>웹 개발 여정</p>
    <a href="/categories/web" class="btn btn--primary" style="display: inline-block; padding: 10px 25px; margin-top: 10px; border-radius: 25px;">더보기</a>
  </div>
  
  <div class="feature__item" style="text-align: center; padding: 30px; border-radius: 15px; background: linear-gradient(145deg, #ffffff, #f0f0f0); box-shadow: 5px 5px 15px #d1d1d1, -5px -5px 15px #ffffff; min-width: 280px;">
    <span style="font-size: 3.5em; margin-bottom: 15px; display: block;">🔍</span>
    <h2 style="font-size: 1.5em; margin: 15px 0;">기타</h2>
    <p style="margin: 15px 0; line-height: 1.6;">개발자의 일상과<br>다양한 기술 이야기</p>
    <a href="/categories/etc" class="btn btn--primary" style="display: inline-block; padding: 10px 25px; margin-top: 10px; border-radius: 25px;">더보기</a>
  </div>
</div>

<div style="background: linear-gradient(145deg, #f8f9fa, #e9ecef); padding: 30px; border-radius: 15px; margin-bottom: 30px;">
  <h2 style="margin-top: 0;">🌟 최근 포스트</h2>
  {% for post in site.posts limit:3 %}
    <div style="margin-bottom: 20px; padding: 15px; background: white; border-radius: 10px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
      <h3 style="margin: 0;"><a href="{{ post.url }}" style="text-decoration: none;">{{ post.title }}</a></h3>
      <p style="margin: 5px 0; color: #666;">{{ post.date | date: "%Y-%m-%d" }}</p>
      {% if post.excerpt %}
        <p style="margin: 10px 0;">{{ post.excerpt | strip_html | truncate: 100 }}</p>
      {% endif %}
    </div>
  {% endfor %}
</div>

<div style="text-align: center; margin-top: 50px; padding: 30px; background: linear-gradient(145deg, #ffffff, #f0f0f0); border-radius: 15px;">
  <h2 style="margin-top: 0;">📊 블로그 통계</h2>
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 20px;">
    <div>
      <h3 style="color: #007bff;">{{ site.posts.size }}</h3>
      <p>총 포스트</p>
    </div>
    <div>
      <h3 style="color: #28a745;">{{ site.categories.size }}</h3>
      <p>카테고리</p>
    </div>
    <div>
      <h3 style="color: #dc3545;">{{ site.tags.size }}</h3>
      <p>태그</p>
    </div>
  </div>
</div>

  

​ 
