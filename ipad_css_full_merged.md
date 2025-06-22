# 🌱 CSS 기본 개념 + iPad 클론 프로젝트 실습 정리

## 1. 🔤 선택자(Selector) 기본

| 문법 | 의미 | 예시 |
|------|------|------|
| `.class` | 클래스 선택자 | `.btn`, `.title` |
| `#id` | ID 선택자 | `#header` |
| `tag` | 태그 선택자 | `body`, `a`, `img` |
| `.parent .child` | 자손 선택자 (띄어쓰기) | `.box img` (박스 안 모든 이미지) |
| `.parent > .child` | 자식 선택자 (>) | `.list > li` (직속 li만) |

---

## 2. 🧱 박스 모델(Box Model)

CSS에서 모든 요소는 **박스 형태**로 구성됨.

```
┌───────────────┐
│   margin      │  ← 바깥 여백
│ ┌───────────┐ │
│ │ padding   │ │  ← 안쪽 여백
│ │ ┌───────┐ │ │
│ │ │ content│ │ │
│ │ └───────┘ │ │
│ └───────────┘ │
└───────────────┘
```

| 속성 | 설명 |
|------|------|
| `margin` | 바깥 여백 |
| `padding` | 내부 여백 |
| `border` | 테두리 |
| `width`, `height` | 콘텐츠 크기 |

---

## 3. 📐 레이아웃 핵심 속성

| 속성 | 설명 |
|------|------|
| `display: flex` | 가로 정렬, 정렬 유연 |
| `justify-content` | 주 축 정렬 (가로) |
| `align-items` | 교차 축 정렬 (세로) |
| `position` | 요소 위치 지정 (`relative`, `absolute`, `fixed`) |
| `z-index` | 위로 쌓이는 순서 지정 |

---

# 💻 iPad 클론 프로젝트 CSS 실습 정리

## ✅ 공통 초기화
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
a {
  text-decoration: none;
  color: inherit;
}
```

## ✅ 전체 페이지 래퍼
```css
.wrap {
  width: 100%;
  overflow-x: hidden;
}
```

## ✅ 헤더 스타일
```css
.header {
  width: 100%;
  padding: 20px 40px;
  position: fixed;
  top: 0;
  background-color: white;
  z-index: 10;
}
```

## ✅ 메인 비주얼 (Hero Section)
```css
.hero {
  height: 100vh;
  background: url('../images/hero.jpg') no-repeat center/cover;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

## ✅ 콘텐츠 이미지 스타일
```css
.section img {
  max-width: 100%;
  height: auto;
}
```

## ✅ 타이틀/텍스트
```css
.title {
  font-size: 48px;
  font-weight: bold;
}
.sub-title {
  font-size: 24px;
  color: #666;
}
```

## ✅ 반응형 미디어 쿼리
```css
@media screen and (max-width: 768px) {
  .title {
    font-size: 32px;
  }
  .sub-title {
    font-size: 18px;
  }
}
```

## ✅ 푸터 스타일
```css
.footer {
  background-color: #f5f5f7;
  padding: 60px 40px;
  text-align: center;
  font-size: 14px;
  color: #888;
}
```

## ✅ 클래스 네이밍 참고

| 클래스 | 역할 |
|--------|------|
| `.wrap` | 전체 래핑 |
| `.header` | 상단 네비 |
| `.hero` | 메인 비주얼 영역 |
| `.section` | 콘텐츠 섹션 |
| `.title`, `.sub-title` | 텍스트 스타일 |
| `.footer` | 하단 정보 영역 |

---

# ✅ 마무리 팁

- `flex`, `margin/padding`, `position`은 퍼블리싱의 핵심입니다.
- 클래스명은 의미 중심(`.hero`, `.title`)으로 명확하게 작성하는 습관을 들이세요.
- 필요할 때 Chrome 개발자도구에서 어떤 CSS가 적용됐는지 **실시간 확인하며 실습**하는 게 최고예요.


---

# 📱 @media와 Breakpoints (반응형 디자인 기초)

## ✅ 미디어 쿼리 기본 문법

```css
@media media-type and (condition) {
  /* CSS 속성 */
}
```

| 항목 | 예시 | 설명 |
|------|------|------|
| `media-type` | `screen`, `print`, `all` | 출력 환경 지정 |
| `condition` | `(max-width: 768px)` | 조건에 따른 스타일 적용 |
| `and` | 논리 연결자 | 여러 조건 연결 가능 |

### 📌 예시:
```css
@media screen and (max-width: 768px) {
  body {
    background-color: #f0f0f0;
  }
}
```

## ✅ 디바이스 방향 조건 (orientation)
```css
@media screen and (orientation: portrait) {
  /* 세로 모드일 때 적용 */
}

@media screen and (orientation: landscape) {
  /* 가로 모드일 때 적용 */
}
```

---

## 📁 CSS 파일 미디어 조건 연결

```html
<!-- 조건별로 다른 CSS 파일을 연결 -->
<link rel="stylesheet" href="style.css" media="screen and (max-width: 1260px)" />
```

---

## 🔁 Breakpoints (중단점)

| 디바이스 | 기준값 | 설명 |
|----------|--------|------|
| PC | ≥ 1001px | 데스크탑 뷰 |
| 태블릿 | ≤ 1000px | 중간 화면 대응 |
| 모바일 | ≤ 740px | 스마트폰 뷰 |

---

## 🎯 가상 클래스 선택자 (Pseudo-classes)

| 선택자 | 설명 |
|--------|------|
| `:hover` | 마우스를 올렸을 때 |
| `:active` | 클릭한 순간 |
| `:focus` | 요소에 포커스 되었을 때 (입력 가능 상태) |

### 📌 `focus` 관련
- `input`, `a`, `button` 등은 기본적으로 포커스 가능
- `tabindex="0"`을 추가하면 다른 요소도 포커스 가능
- `tabindex="-1"`은 포커스는 가능하지만 Tab 키로 접근 불가

> 📌 참고: [HTML 대화형 콘텐츠 목록 - MDN](https://developer.mozilla.org/ko/docs/Web/Guide/HTML/Content_categories#interactive_content)

