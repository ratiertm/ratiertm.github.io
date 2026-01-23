# Hugo 블로그 가이드

## 사이트 정보

- **사이트 주소**: https://ratiertm.github.io/
- **저장소**: https://github.com/ratiertm/ratiertm.github.io
- **테마**: Blowfish
- **빌드 도구**: Hugo + GitHub Actions

---

## GitHub Actions 자동 빌드 설정

### 작동 원리

```
git push → GitHub Actions 자동 실행 → Hugo 빌드 → GitHub Pages 배포
```

### 설정 파일 위치

`.github/workflows/hugo.yml`

### GitHub Pages 설정

1. 저장소 Settings → Pages 이동
2. Build and deployment → Source: **GitHub Actions** 선택

---

## 글 작성 방법

### 방법 1: 로컬에서 작업 (터미널)

```bash
# 1. 프로젝트 폴더로 이동
cd ratiertm-hugo

# 2. 새 글 작성 (content/posts/ 폴더에 .md 파일 생성)

# 3. 파일 추가
git add .

# 4. 커밋
git commit -m "새 글 추가"

# 5. GitHub에 push
git push origin main
```

### 방법 2: GitHub 웹사이트에서 직접 업로드

1. https://github.com/ratiertm/ratiertm.github.io 접속
2. `content/posts` 폴더 클릭
3. **Add file → Upload files** 클릭
4. MD 파일 드래그 & 드롭
5. 하단 **Commit changes** 클릭

### 방법 3: GitHub 웹사이트에서 직접 작성

1. https://github.com/ratiertm/ratiertm.github.io 접속
2. `content/posts` 폴더 클릭
3. **Add file → Create new file** 클릭
4. 파일명 입력 (예: `2026-01-25-새글제목.md`)
5. 내용 작성
6. **Commit changes** 클릭

---

## MD 파일 형식

### 기본 템플릿

```markdown
---
title: "글 제목"
description: "글 설명"
date: 2026-01-24
tags: [태그1, 태그2]
category: 카테고리명
author: 작성자
---

# 본문 제목

본문 내용 작성...
```

### Front Matter 필수 항목

| 항목 | 설명 | 예시 |
|------|------|------|
| title | 글 제목 | "NVIDIA 분석" |
| date | 작성일 | 2026-01-24 |

### Front Matter 선택 항목

| 항목 | 설명 | 예시 |
|------|------|------|
| description | 글 요약 | "NVIDIA 투자 분석" |
| tags | 태그 목록 | [NVDA, AI, 투자] |
| category | 카테고리 | 미국주식 |
| author | 작성자 | 마인드빌드 |
| draft | 초안 여부 | true/false |

---

## Shortcode 사용법

### 하이라이트 박스

```markdown
{{< highlight-box >}}
강조할 내용
{{< /highlight-box >}}
```

### 팁 박스

```markdown
{{< tip-box >}}
팁 내용
{{< /tip-box >}}
```

### 경고 박스

```markdown
{{< warning-box >}}
경고 내용
{{< /warning-box >}}
```

### 통계 박스

```markdown
{{< stat-box number="73%" >}}
설명 텍스트
{{< /stat-box >}}
```

### 색상 텍스트

```markdown
{{< color "red" >}}빨간 텍스트{{< /color >}}
{{< color "#3498DB" >}}파란 텍스트{{< /color >}}
```

---

## 로컬 미리보기

```bash
# 프로젝트 폴더에서 실행
hugo server -D

# 브라우저에서 접속
# http://localhost:1313/
```

---

## 빌드 상태 확인

- **GitHub Actions**: https://github.com/ratiertm/ratiertm.github.io/actions
- 녹색 체크: 성공
- 빨간 X: 실패 (로그 확인 필요)

---

## 문제 해결

### 빌드 실패 시

1. Actions 페이지에서 실패한 workflow 클릭
2. 에러 로그 확인
3. MD 파일의 front matter 형식 확인 (YAML 문법 오류 주의)

### 사이트가 안 보일 때

1. GitHub Actions 빌드 완료 확인
2. 브라우저 캐시 삭제 또는 시크릿 창에서 접속
3. 배포까지 1-2분 소요될 수 있음

---

## 폴더 구조

```
ratiertm-hugo/
├── .github/workflows/hugo.yml  # GitHub Actions 설정
├── content/posts/              # 블로그 글 (MD 파일)
├── layouts/shortcodes/         # 커스텀 shortcode
├── static/                     # 정적 파일 (이미지 등)
├── themes/blowfish/            # 테마
└── hugo.toml                   # Hugo 설정
```
