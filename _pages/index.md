---
layout: single # 원하는 레이아웃, 예: single, splash 
title: ""
permalink: /
author_profile: true
sidebar_main: true
classes: wide
---

<!-- 전체 컨테이너 시작 - 모든 섹션을 감싸는 컨테이너 -->
<div style="max-width: 1100px; margin: 0 auto; padding: 20px;">

  <!-- 개발자 에티켓 섹션 - 웜톤 배경색 변경 -->
  <div style="background: linear-gradient(135deg, #fff9f0, #ffefd5); padding: 30px; border-radius: 12px; margin-bottom: 30px; box-shadow: 0 3px 10px rgba(0,0,0,0.08);">
    <h2 style="margin-top: 0; margin-bottom: 25px; color: #5a3e2f; font-size: 1.8em; border-bottom: 2px solid rgba(230, 126, 34, 0.2); padding-bottom: 10px;"> 개발자의 에티켓 </h2>
    <div style="display: flex; flex-direction: column; gap: 12px;">
      <div style="background: rgba(255, 255, 255, 0.7); padding: 15px; border-radius: 8px; display: flex; align-items: center; backdrop-filter: blur(5px);">
        <span style="font-size: 1.5em; margin-right: 15px; color: #e67e22;">🤔</span>
        <p style="margin: 0; color: #5a3e2f; font-size: 1em;"><strong>1.</strong> 별거 아닌 거에 "어?" 금지</p>
      </div>
      <div style="background: rgba(255, 255, 255, 0.7); padding: 15px; border-radius: 8px; display: flex; align-items: center; backdrop-filter: blur(5px);">
        <span style="font-size: 1.5em; margin-right: 15px; color: #e67e22;">👥</span>
        <p style="margin: 0; color: #5a3e2f; font-size: 1em;"><strong>2.</strong> 한 사람 뒤에 세 명 이상 서있기 금지</p>
      </div>
      <div style="background: rgba(255, 255, 255, 0.7); padding: 15px; border-radius: 8px; display: flex; align-items: center; backdrop-filter: blur(5px);">
        <span style="font-size: 1.5em; margin-right: 15px; color: #e67e22;">🤫</span>
        <p style="margin: 0; color: #5a3e2f; font-size: 1em;"><strong>3.</strong> 모니터 쳐다보며 웅성웅성 금지</p>
      </div>
    </div>
  </div>

  <!-- 최근 포스트 섹션 - 웜톤 배경색 변경 -->
  <div style="background: linear-gradient(135deg, #fff5e6, #ffe8cc); padding: 30px; border-radius: 12px; margin-bottom: 30px; box-shadow: 0 3px 10px rgba(0,0,0,0.08);">
    <h2 style="margin-top: 0; margin-bottom: 25px; color: #5a3e2f; font-size: 1.8em; border-bottom: 2px solid rgba(230, 126, 34, 0.2); padding-bottom: 10px;">최근 포스트</h2>
    {% for post in site.posts limit:3 %}
      <div style="margin-bottom: 20px; padding: 15px; background: rgba(255, 255, 255, 0.7); border-radius: 8px; backdrop-filter: blur(5px);">
        <h3 style="margin: 0; font-size: 1.3em;"><a href="{{ post.url }}" style="text-decoration: none; color: #d35400;">{{ post.title }}</a></h3>
        <p style="margin: 5px 0; color: #7f6a56; font-size: 0.9em;">{{ post.date | date: "%Y-%m-%d" }}</p>
        {% if post.excerpt %}
          <p style="margin: 10px 0; color: #5a3e2f;">{{ post.excerpt | strip_html | truncate: 100 }}</p>
        {% endif %}
      </div>
    {% endfor %}
    <div style="text-align: right; margin-top: 15px;">
      <a href="/year-archive/" style="text-decoration: none; color: #d35400; font-weight: 500;">모든 포스트 보기 →</a>
    </div>
  </div>

  <!-- 주요 카테고리 섹션 - 웜톤 배경색 변경 -->
  <div style="background: linear-gradient(135deg, #fff0e6, #ffe0cc); padding: 30px; border-radius: 12px; margin-bottom: 30px; box-shadow: 0 3px 10px rgba(0,0,0,0.08);">
    <h2 style="margin-top: 0; margin-bottom: 25px; color: #5a3e2f; font-size: 1.8em; border-bottom: 2px solid rgba(230, 126, 34, 0.2); padding-bottom: 10px;">주요 카테고리</h2>
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;">
      <div style="text-align: center; padding: 25px; border-radius: 8px; background: rgba(255, 255, 255, 0.7); backdrop-filter: blur(5px); transition: transform 0.3s ease, box-shadow 0.3s ease;" onmouseover="this.style.transform='translateY(-5px)';this.style.boxShadow='0 8px 15px rgba(0,0,0,0.1)';" onmouseout="this.style.transform='translateY(0)';this.style.boxShadow='none';">
        <span style="font-size: 2.5em; margin-bottom: 15px; display: block; color: #e67e22;">🎮</span>
        <h3 style="font-size: 1.4em; margin: 10px 0; color: #5a3e2f;">게임 개발</h3>
        <a href="/categories/game" class="btn" style="display: inline-block; padding: 8px 25px; margin-top: 15px; border-radius: 25px; background-color: #e67e22; color: white; text-decoration: none; font-weight: 500; transition: background-color 0.3s ease;">더보기</a>
      </div>
      
      <div style="text-align: center; padding: 25px; border-radius: 8px; background: rgba(255, 255, 255, 0.7); backdrop-filter: blur(5px); transition: transform 0.3s ease, box-shadow 0.3s ease;" onmouseover="this.style.transform='translateY(-5px)';this.style.boxShadow='0 8px 15px rgba(0,0,0,0.1)';" onmouseout="this.style.transform='translateY(0)';this.style.boxShadow='none';">
        <span style="font-size: 2.5em; margin-bottom: 15px; display: block; color: #e67e22;">💻</span>
        <h3 style="font-size: 1.4em; margin: 10px 0; color: #5a3e2f;">웹 개발</h3>
        <a href="/categories/web" class="btn" style="display: inline-block; padding: 8px 25px; margin-top: 15px; border-radius: 25px; background-color: #e67e22; color: white; text-decoration: none; font-weight: 500; transition: background-color 0.3s ease;">더보기</a>
      </div>
      
      <div style="text-align: center; padding: 25px; border-radius: 8px; background: rgba(255, 255, 255, 0.7); backdrop-filter: blur(5px); transition: transform 0.3s ease, box-shadow 0.3s ease;" onmouseover="this.style.transform='translateY(-5px)';this.style.boxShadow='0 8px 15px rgba(0,0,0,0.1)';" onmouseout="this.style.transform='translateY(0)';this.style.boxShadow='none';">
        <span style="font-size: 2.5em; margin-bottom: 15px; display: block; color: #e67e22;">🔍</span>
        <h3 style="font-size: 1.4em; margin: 10px 0; color: #5a3e2f;">기타</h3>
        <a href="/categories/etc" class="btn" style="display: inline-block; padding: 8px 25px; margin-top: 15px; border-radius: 25px; background-color: #e67e22; color: white; text-decoration: none; font-weight: 500; transition: background-color 0.3s ease;">더보기</a>
      </div>
    </div>
  </div>

</div><!-- 전체 컨테이너 끝 -->

  

​ 
