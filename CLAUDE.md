# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

스텝업파트너스의 면접 안내 페이지 모음. 후보자별로 맞춤 제작된 HTML 페이지를 GitHub Pages로 배포한다.

배포 베이스 URL: `https://withusps-coder.github.io/interview-guides/`

## 파일 구조 규칙

- 클라이언트사별 폴더 생성 (예: `ablearn/`)
- HTML 파일명은 면접일 기준 `YYMMDD.html` 형식 (예: `250327.html`)
- 새 파일 추가 후 반드시 `README.md`의 표에 링크 행을 추가한다

## README.md 표 형식

```markdown
| 후보자 | 포지션 | 면접일 | 링크 |
|--------|--------|--------|------|
| 이름 | 포지션명 | YYYY.MM.DD (요일) | [바로가기](https://withusps-coder.github.io/interview-guides/{폴더}/{파일명}.html) |
```

## HTML 페이지 구조

각 면접 안내 페이지는 단일 self-contained HTML 파일로 구성된다:

- **테마**: CSS 변수 기반 라이트/다크 모드 (`html.theme-light` / `html.theme-dark`)
- **폰트**: Google Fonts — Noto Sans KR + Inter
- **외부 의존성**: `html-to-image` (CDN) — 이미지 저장 기능용
- **메뉴**: 우상단 고정 버튼 — 다크모드 토글, 이미지 저장
- **애니메이션**: `reveal` 클래스 + IntersectionObserver로 스크롤 진입 시 페이드인
- **접근성**: `.skip-to-content`, `aria-label`, `role` 속성 포함
- **인쇄**: `@media print` 최적화 포함

## 배포

별도 빌드 과정 없음. `main` 브랜치에 push하면 GitHub Pages가 자동 배포된다.

```bash
git add {파일}
git commit -m "메시지"
git push origin main
```
