---
layout: single
title: "[GitHub Blog] Jekyll 기반 깃허브 블로그 시작하기"
categories: blog
tags: [GitHub Pages, Jekyll, minimal-mistakes, 블로그]
toc: true
author_profile: true
toc_sticky: true
toc_label: "목차"
typora-root-url: ../
---



##  Jekyll 기반 깃허브 블로그minimal-mistakes 테마 

![minimal-mistakes 테마](/assets/images/2024-01-16-first-post/minimal_mistakes.png)
*현재 사용 중인 minimal-mistakes 테마의 기본 레이아웃*   



## 💻 로컬 서버 설정

블로그 변경사항을 실시간으로 확인하기 위한 로컬 서버 설정 방법입니다.

```bash
# 1. 레포지토리 디렉토리로 이동
cd C:\Blog\hoyoung1359.github.io

# 2. 로컬 서버 실행 (실시간 리로드 옵션 포함)
bundle exec jekyll serve --livereload

# 3. 브라우저에서 확인
http://localhost:4000/ 접속
```

> 💡 **TIP**: `--livereload` 옵션을 사용하면 파일 변경 시 자동으로 페이지가 새로고침됩니다.

## 🎨 테마 커스터마이징

### 1. 폰트 설정

```scss
// _sass/minimal-mistakes.scss
@import url('https://fonts.googleapis.com/css2?family=원하는+폰트&display=swap');

// _sass/_variables.scss
$글씨체-변수: "폰트명", fallback-폰트;
```

### 2. 글씨 크기 조정

```scss
// _sass/_reset.scss
html {
  @include breakpoint($medium) {
    font-size: 18px;  // 중간 크기 화면
  }

  @include breakpoint($large) {
    font-size: 20px;  // 큰 화면
  }

  @include breakpoint($x-large) {
    font-size: 22px;  // 매우 큰 화면
  }
}
```

### 3. 프로필 설정

```scss
// _sass/_sidebar.scss
.author__avatar {
  img {
    max-width: 150px;  // 프로필 이미지 크기
    border-radius: 50%;  // 원형 이미지
  }
}
```

### 4. 본문 레이아웃 조정

```scss
// _sass/_variables.scss
$x-large: 1400px;  // 최대 너비 조정
$right-sidebar-width-narrow: 200px;  // 사이드바 너비
$right-sidebar-width: 300px;
```

## 📝 포스트 작성 팁

### 이미지 추가
- 이미지는 `/assets/images/포스트-이름/` 디렉토리에 저장
- 마크다운 문법으로 삽입:
```markdown
![이미지설명](/assets/images/2024-01-16-first-post/example.png)
```

### 목차 설정
```yaml
---
toc: true           # 목차 사용
toc_sticky: true    # 목차 고정
toc_label: "목차"   # 목차 제목
---
```

## 🔍 유용한 설정들

1. **사이드바 프로필**: `author_profile: true`로 설정
2. **포스트 네비게이션**: 이전/다음 포스트 이동
3. **카테고리/태그**: 포스트 분류와 검색 용이
4. **댓글 기능**: Disqus 등 댓글 시스템 연동



> 🎯 **참고**: 더 자세한 Jekyll 테마 커스터마이징은 [공식 문서](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)를 참조하기

