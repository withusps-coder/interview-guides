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

## PIN 게이트 (필수)

모든 면접 안내 HTML 파일에는 반드시 PIN 게이트를 포함한다. `ablearn/250327_test.html`을 레퍼런스로 사용한다.

### 구현 방식
- 스텝업파트너스 로고(`/Users/kms/Downloads/기업 로고/스텝업파트너스 로고_배경 제거.png`)를 base64로 인라인 임베드
- 로고에 `filter: brightness(0) invert(1)` 적용 (다크 배경용 흰색 처리)
- PIN은 면접일 기준 `MMDD` 4자리 (예: 3월 27일 → `0327`)
- 4개 개별 블록 입력 방식 (`maxlength="1"` 인풋 4개)
- 마지막 자리 입력 시 자동 확인, 붙여넣기 지원
- 정답 시 `sessionStorage`에 저장 (새로고침 시 재입력 불필요)
- 오답 시 shake 애니메이션 + 입력값 초기화

### 주요 스타일 값
- 로고 높이: `44px`
- 제목(`면접 안내 페이지`) 폰트: `1.3rem`
- 부제(`접근 코드를 입력해주세요.`) 폰트: `0.95rem` — **마침표 반드시 포함**
- 문구 아래 간격(`.pin-sub margin-bottom`): `28px`
- 박스 아래 간격(`.pin-digits margin-bottom`): `40px`

### README 기재 시
- 후보자 이름은 `성**` 형식으로 블라인드 처리
- PIN은 README에 기재하지 않고 후보자에게 별도 전달

## 배포

별도 빌드 과정 없음. `main` 브랜치에 push하면 GitHub Pages가 자동 배포된다.

```bash
git add {파일}
git commit -m "메시지"
git push origin main
```
