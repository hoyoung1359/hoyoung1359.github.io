---
layout: single
title:  "[깃허브 블로그] 블로그 생성"
categories: blog
toc: true
author_profile: true
toc: true
toc_sticky: true
toc_label: 목차
typora-root-url: ../
---

# 깃허브 블로그 커스텀

로컬 서버로 블로그 변동사항 테스트:   

1. cd C:\Blog\hoyoung1359.github.io   (레포지토리로 이동)   

2. bundle exec jekyll serve --livereload      

3. http://localhost:4000/ 접속.  

	

폰트변경:   
    구글폰트 minimal-mistakes.scss 밑에 import한 후 _variable.scss 에서 글시체 설정  

글씨크기조정:  
	_reset.scss 에서 breakpoint에 따른 크기 조정

프로필변경:   
	_sidebar.scss: .author_avatar에서 프로필 사진 크기 변경가능     



본문간격조정:  
_variable.scss: x-large 조정, 본문 간격 조정  



이미지:   
/assets/images 에 저장후 추가  



목차:  
	toc: 목차
	toc_sticky: 목차 고정
	tock_labe: 목차 이름(아이콘도 변경가능하다고 함)

​						

jekyll 테마: minimal-mistakes

<img src="/assets/images/2024-01-16-first-post/minimal_mistakes.png" alt="minimal_mistakes" style="zoom:80%;" />

