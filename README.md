# how to use CSS
***

## CSS

- Cascading Style Sheets
- Cascading: 여러 스타일 규칙이 있을 때, 우선 순위를 통해 스타일이 적용되는 방식
- 웹 페이지의 스타일과 레이아웃을 정의하는 언어
- HTML이 정의한 페이지의 구조에 색상, 글꼴, 간격, 배치 등 시각적 요소를 추가하여 웹 페이지의 디자인을 담당

***

## Syntax

---

### 기본 구조
```
선택자 {
    속성: 값;
}
```
```
h1 { color: yellow; font-size: 2em; }
```
- 선택자 (Selector)
    - `h1`
    - 스타일을 적용할 HTML 요소
- 속성 (Property)
    - `color`, `font-size`
    - 적용할 스타일의 종류
- 값 (Value)
    - `yellow`, `2em`
    - 속성에 지정할 실제 값
- 선언 (Declaration)
    - `color: yellow`, `font-size: 2em`
    - 속성과 값을 하나의 단위로 묶은 것
    - 속성에 대해 값을 설정하는 부분
    - `속성: 값` 의 형태
- 선언부 (Declaration Block)
    - `{ color: yellow; font-size: 2em; }`
    - 중괄호 안에 있는 모든 선언
    - 여러 선언을 중괄호로 감싸고, 각 선언은 세미콜론으로 구분
    - 스타일 규칙을 정의하는 실제 내용이 들어 있는 부분
- 규칙 (Rule)
    - `h1 { color: yellow; font-size: 2em; }`
    - 선택자와 선언부를 합친 전체
- 세미콜론 (;)
    - 각 속성과 값을 구분할 때 사용
    - 다음 속성에 존재할 것을 대비해, 마지막 선언 뒤에도 세미콜론을 쓰는 것이 좋음, 필수 아님
- 공백
    - 속성명과 값사이, 선택자와 중괄호 사이에는 가독성을 위해 보통 공백을 추가, 필수아님
- 개행
    - 선택자와 선언부 사이, 선언과 선언 사이는 앞뒤로 개행 가능
    - 속성명과 속성값 사이에는 개행 불가

---

### HTML 속성과 CSS 속성

|구분|HTML 속성|CSS 속성|
|-|-|-|
|목적|HTML 요소의 기능과 동작을 설정|HTML 요소의 스타일을 설정|
|위치|HTML 태그 내|CSS 파일 또는 `<style>` 태그 내 또는 인라인|
|적용 대상|HTML 요소의 구조적 속성을 정의|HTML 요소의 디자인 및 레이아웃을 설정|
- HTML 속성은 Attribute
- CSS 속성은 Property

---

### 주석

```
/* 주석 */
```
- `/*`로 시작, `*/`로 끝남

---

### 스타일 정의 방법

#### Inline

- 해당 요소에 직접 `style` 속성을 이용해서 규칙을 선언하는 방법
- 해당 요소에 직접 입력하기 때문에 선택자가 필요하지 않음
- 다른 요소에 영향을 주지 않고, 한 요소에만 적용
- 우선순위가 높아서, 외부 또는 내부 스타일 시트보다 우선적으로 적용
- 유지보수가 어려우며, 재활용이 되지 않음
```
<div style="color: red;"> 내용 </div>
```

#### Internal

- 문서 내의 `<style>`태그 안에 스타일을 정의
- `<style>`은 `<head>`태그 내부에 위치
- 스타일이 HTML 문서 내에 포함
- HTML 문서 내 모든 요소에 적용 가능
- 여러 페이지에 동일한 스타일을 공유하려면, 각 페이지에 `<style>`태그를 포함해야 함
```
<html>
    <head>
        <style>
            div {
                color: red;
            }
        </style>
    </head>
    <body>
        내용
    </body>
</html>
```

#### External

- 스타일을 별도의 `.css` 파일에 정의, HTML 문서에서 그 파일을 링크
- 다수의 HTML 문서에서 동일한 스타일을 공유 가능
- 페이지 로딩 속도에 도움, 코드가 분리되어 가독성 향상
- 유지보수와 관리 용이
- 순서
    1. `.css`파일을 만들고 내부에 스타일 규칙을 선언
    2. `<head>`태그 내에 `<link>`를 선언 후 `href`속성에 CSS 파일의 경로 지정
    ```
        <link rel="stylesheet" href="style.css">
    ```
    - `rel`
        - 연결되는 파일이 문서와 어떤 관계인지 명시하는 속성, 필수 속성
        - Relationship의 약자
        - CSS 파일은 `stylesheet`로 설정해야 함
    - `href`
        - 연결할 외부 스타일 시트 파일의 경로 지정, 필수 속성
        - Hypertext Reference의 약자
        - CSS 파일의 경로를 상대 경로나 절대 경로로 지정 가능
    - `type`
        - 연결된 리소스이 MIME 타입을 정의
            - _MIME 타입: 인터넷에서 전송되는 파일이나 데이터의 형식을 지정하는 표준_
        - CSS 파일은 `text/css`로 설정
    - `media`
        - CSS 파일이 적용될 조건을 설정
        - 특정 화면 크기나 장치에서만 스타일을 적용 가능
    - `title`
        - 스타일 시트에 이름을 붙여줌
        - 페이지에서 여러 스타일 시트를 사용할 때 각 스타일 시트의 역할을 구분하기 위함
        - 예를 들어, 웹 페이지에서 다국어 버전마다 다른 스타일을 적용할 때
    - `as`
        - 브라우저가 리소스를 미리 로딩할 때 어떤 리소스인지 알려주는 역할
        - 주로 `preload`와 함께 사용
        - 성능 최적화를 위해 사용 가능
    - `crossorigin`
        - 교차 출처 리소스(CORS)를 처리
        - 다른 출처에서 로드된 스타일 시트에 대해 CORS 정책 사용 가능
            - _CORS 정책: 교차 출처 리소스 공유(Cross-Origin Resource Sharing), 웹 보안 기능중 하나, 다른 도메인이나 출처(origin)에서 제공되는 리소스에 접근할 때 브라우저가 이를 허용하거나 차단하는 정책_
        - 보통 외부 CDN에서 제공하는 리소스를 사용할 때 유용
            - _CDN: 콘텐츠 전송 네트워크(Content Delivery Network)_

#### Import

- 스타일 시트 내에서 다른 스타일 시트 파일을 불러오는 방식
- 여러 CSS 파일을 하나로 합치지 않고도, 여러 파일을 관리 가능
```
@import url("style.css");
```
- `@import`는 CSS 파일을 불러오는 요청을 추가로 발생시켜 페이지 로딩 속도에 영향을 줄 수 있음
- 성능의 이유로 `@import`보다는 `<link>`태그를 선호

***

## 선택자 (Selector)

- 스타일을 적용할 HTML 요소를 선택하는 역할

---

### 요소 선택자 (Element Selector)

- 특정 HTML 태그에 스타일을 적용
- 태그 선택자라고도 함
- 문서 내에 선택자에 해당하는 모든 요소에 스타일 규칙이 적용
```
p {
    color: blue;
}
```

---

### 그룹화 선택자 (Grouping Selector)

- 여러 선택자를 한 번에 묶어서 스타일을 적용 가능
- `,`쉼표로 구분
```
h1, h2, h3 {
    color: green;
}
```

---

### 전체 선택자 (Universal Selector)

- 모든 HTML 요소를 선택하는 선택자
- `*`asterisk 기호 사용
```
* {
    color: red;
}
```

---

### 클래스 선택자 (Class Selector)

- 특정 클래스가 적용된 모든 요소에 스타일을 적용
- `.`을 사용하여 클래스를 선택
- 여러 요소에 같은 클래스를 넣고 같은 규칙 적용 가능
```
.yes {
    font-size: 10px;
    color: orange;
}
```

---

### 아이디 선택자 (Id Selector)

- 특정 ID를 가진 요소에 스타일을 적용
- `#`을 사용하여 아이디를 선택
- ID는 문서 내에서 유일하므로 ID 선택자로 규칙을 적용할 수 있는 요소는 단 하나
```
#bar {
    background-color: yellow;
}
```

---

### 속성 선택자 (Attribute Selector)

- HTML 요소의 속성을 기준으로 스타일을 적용할 수 있는 CSS 선택자
- 특정 속성이나 속성 값이 일치하는 요소를 선택 가능
- `[ ]`대괄호를 사용하여 구현
- `속성`만 넣거나 `속성=값`을 넣음
```
p[class][id] {
    color: red;
}
```

---

### 부분 속성값으로 선택

- `[class~="bar"]`: class 속성의 값이 공백으로 구분한 "bar" 단어가 포함되는 요소 선택
- `[class^="bar"]`: class 속성의 값이 "bar"로 시작하는 요소 선택
- `[class$="bar"]`: class 속성의 값이 "bar"로 끝나는 요소 선택
- `[class*="bar"]`: class 속성의 값에 "bar"문자가 포함되는 요소 선택

---

### 선택자의 조합

- 요소와 클래스의 조합
    - `p.bar{...}`
- 다중 클래스
    - `.foo.bar{...}`
- 아이디와 클래스의 조합
    - `#foo.bar{...}`

---

### 문서 구조 관련 선택자

#### 부모와 자식, 조상과 자손, 형제
```
<html>
    <body>
        <div>
            <h1><span>HTML</span>: Hyper Text Markup Language</h1>
        </div>
        <p>HTML, CSS, Javascript</P>
    <body>
</html>
```
- 부모(Parent) 요소
    - 해당 요소를 포함하는 가장 가까운 상위 요소
    - 부모 요소는 자식 요소를 감싸고 있음
    - `<body>`의 부모 요소: `<html>`
    - `<div>`,`<p>`의 부모 요소: `<body>`
    - `<h1>`의 부모 요소: `<div>`
    - `<span>`의 부모 요소: `<h1>`
- 자식(Child) 요소
    - 해당 요소가 포함하는 가장 가까운 하위 요소
    - 구조 적으로 자식 요소는 부모 요소의 바로 아래에 위치
    - `<html>`의 자식 요소: `<body>`
    - `<body>`의 자식 요소: `<div>`, `<p>`
    - `<div>`의 자식 요소: `<h1>`
    - `<h1>`의 자식 요소: `<span>`
- 조상(Ancestor) 요소
    - 해당 요소를 포함하는 모든 상위 요소
    - `<body>`의 조상 요소: `<html>`
    - `<div>`, `<p>`의 조상 요소: `<body>`, `<html>`
    - `<h1>`의 조상 요소: `<div>`,`<body>`, `<html>`
    - `<span>`의 조상 요소: `<h1>`, `<div>`, `<body>`, `<html>`
- 자손(Descendant) 요소
    - 해당 요소가 포함하는 모든 하위 요소
    - `<html>`의 자손 요소: `<body>`, `<div>`, `<p>`, `<h1>`, `<span>`
    - `<body>`의 자손 요소: `<div>`, `<p>`, `<h1>`, `<span>`
    - `<div>`의 자손 요소: `<h1>`, `<span>`
    - `<h1>`의 자손 요소: `<span>`
- 형제(Sibling) 요소
    - 같은 부모를 갖는 요소
    - `<div>`,`<p>`
    - 인접한(Adjacent) 형제
        - 해당 요소 바로 뒤에 있는 첫 번째 형제 요소
        - `<div>`,`<p>`

#### 자손 선택자
```
div span {
    color: red;
}
```
- 특정 요소 내에 있는 모든 자손 요소에 스타일을 적용
- 선택자 사이에 아무 기호 없이 공백으로 구분
- `<div>`의 자손 요소인 모든 `<span>`을 선택하는 선택자

#### 자식 선택자
```
div > h1 {
    color: red;
}
```
- 특정 요소의 직접적인 자식 요소에 스타일을 적용
- 선택자 사이에 `>`로 구분
- `<div>`의 자식 요소인 모든 `<h1>`을 선택하는 선택자

#### 일반 형제 선택자
```
div ~ p {
    color: red;
}
```
- 특정 요소 이후에 나오는 모든 형제 요소에 스타일을 적용
- 선택자 사이에 `~`로 구분
- `<div>`의 형제 요소인 모든 `<p>`를 선택하는 선택자

#### 인접 형제 선택자
```
div + p {
    color: red;
}
```
- 특정 요소 바로 뒤에 오는 형제 요소에 스타일을 적용
- 선택자 사이에 `+`로 구분
- `<div>`의 바로 뒤에 오는 첫 번째 형제 요소인 `<p>`를 선택하는 선택자

#### 부모, 자식, 조상, 자손, 형제 선택자의 조합
```
html > body div + p {...}
```
- `<html>`의 자식인 `<body>`의 자손인 `<div>`와 인접한 형제 선택자 `<p>`를 선택

---

### 가상 선택자

- Pseudo Selector
- HTML 요소의 상태나 구조에 따라 스타일을 적용할 수 있는 특수한 선택자

#### 가상 클래스

- Pseudo Class
- 요소의 상태나 특정 조건에 따라 스타일을 적용
- 미리 정의해 놓은 상황에 적용되도록 약속된 보이지 않는 가상의 클래스
- `:`기호로 구분
    ```
    button:hover{
        color: red;
    }
    ```
1. 문서 구조와 관련된 가상 클래스
    - `:first-child`: 첫 번째 자식 요소 선택
    - `:last-child`: 마지막 자식 요소 선택
2. 앵커 요소와 관련된 가상 클래스
    - `:link`: 하이퍼링크이면서 아직 방문하지 않은 앵커
    - `:visited`: 이미 방문한 하이퍼링크
    - 하이퍼링크는 앵커 요소에 `href` 속성이 있는 것을 의미
3. 사용자 동작과 관련된 가상 클래스
    - `:focus`: 현재 입력 초점을 가진 요소
    - `:hover`: 마우스 포인터가 있는 요소
    - `:active`: 사용자 입력으로 활성화된 요소

#### 가상 요소

- Pseudo Element
- 요소의 특정 부분이나 그 외의 부분을 선택하여 스타일을 적용
- HTML 코드에 존재하지 않는 구조 요소에 스타일을 적용
- `::`기호로 구분 (CSS3 이전에는 `:`로 구분)
- `::before`: 가장 앞에 요소를 삽입
- `::after`: 가장 뒤에 요소를 삽입
- `::first-line`: 요소의 첫 번째 줄에 있는 텍스트
- `::first-letter`: 블록 레벨 요소의 첫 번째 문자

---

### 구체성

- Specificity
- 스타일 규칙이 충돌할 때, 어떤 규칙이 우선으로 적용될지 결정하는 우선순위 규칙
- 선택자를 얼마나 명시적으로(구체적으로) 선언했느냐를 수치화한 것
- 구체성이 더 높은 선택자가 우선으로 적용
- 구체성 점수 계산
    - 1, 0, 0, 0 : 인라인 스타일
        - CSS 파일이나 스타일 태그보다 우선 적용
    - 0, 1, 0, 0 : ID 선택자
    - 0, 0, 1, 0 : 클래스 선택자, 속성 선택자, 가상 클래스
    - 0, 0, 0, 1 : 태그 선택자, 가상 요소
    ```
    #page {...} /* 0,1,0,0 */
    p#page {...} /* 0,1,0,1 */
    ```
- `!important`
    - 별도의 구체성 값은 없지만, 모든 구체성을 무시하고 강제적으로 우선순위를 부여
    - 속석값 뒤 한 칸 공백을 주고 `!`기호와 함께 사용
    ```
    p {
        color: red !important;
    }
    ```

---

### 상속

- Inheritance
- 부모 요소가 자식 요소에게 스타일 속성을 자동으로 전달하는 개념
- 텍스트 관련 속성(`color`,`font-family`,`font-size`등)은 상속
- 레이아웃 관련 속성(`margin`,`padding`,`border`등)은 상속되지 않음
- `inherit`: 특정 속성이 부모 요소에서 상속되도록 강제로 설정
- `initial`: 해당 속성을 기본값(브라우저의 기본 스타일)으로 초기화
- `unset`: 만약 상속되는 속성이라면 부모로부터 상속하고, 그렇지 않으면 기본값으로 설정
```
div {
    color: red;
}
p {
    color: inherit;
}
span {
    color: unset;
}
```

---

### 캐스케이딩

- Cascading
- 스타일이 적용되는 과정에서 우선순위를 결정하는 중요한 규칙
- CSS 규칙이 적용되는 순서
    1. 중요도(`!important`)
    2. 구체성 점수
    3. 선언 순서
        - 동일한 구체성을 가진 규칙이 여러개 있을 경우, 나중에 선언된 규칙이 우선 적용

---

### 선택자 레퍼런스

- [https://www.w3schools.com](https://www.w3schools.com/cssref/css_selectors.php)

***

## 속성

- HTML 요소의 스타일을 정의
- `속성명: 값` 형태로 작성

---

### CSS reference를 통해 확인 가능한 사항

- 속성명: HTML 요소에 적용할 스타일을 지정하는 속성을 나타내는 이름
- 속성값: 해당 속성이 어떤 스타일을 적용할지 결정하는 값
    - Initial: 초기값, 속성의 기본값
    - Inherit: 부모 요소의 해당 속성 값을 적용 (상속 가능할 요소일 경우)
- 지원 범위
    - 해당 속성이 정의에 맞게 동작 가능한 CSS 버전, 브라우저별 버전
    - 어떤 브라우저의 어떤 버전이냐에 따라 같은 값이어도 다르게 렌더링 됨
- 예제
    - 문법과 속성값을 바탕으로 실제로 속성이 동작하는 예제 코드
- 참고사항
    - 해당 속성에 대한 특이사항이나 버그

---

### CSS reference

- [https://www.w3.org](https://www.w3.org)
- [https://www.w3schools.com](https://www.w3schools.com)
- [https://developer.mozilla.org](https://developer.mozilla.org)

---

### 단위

- 스타일을 적용할 때 사용하는 측정 기준
- 절대 길이 단위와 상대 길이 단위로 구분

#### 절대 길이 단위

- 물리적인 크기나 고정된 크기를 기준으로 설정
- 화면 크기나 부모 요소의 크기에 영향을 받지 않음
- px (픽셀)
    - 화면의 픽셀 크기를 기준으로 한 고정된 단위
    - 화면 해상도나 화면 크기와 관계 없이 고정된 크기를 유지
    - 장치의 해상도에 따라 상대적
    - 여러 환경에서 디자인을 같게 표현하고, 브라우저 호환성에 유리한 구조
    - 디자인 의도가 많이 반영된 웹사이트의 경우, 픽셀 단위를 사용하는 것을 권장
    - 1px = 1/96 of 1 inch
- pt (포인트)
    - 인쇄물이나 워드프로세서 프로그램에서 사용된 가장 작은 표준 인쇄단위
    - 화면 해상도나 화면 크기와 관계 없이 고정된 크기를 유지
    - 장치의 해상도에 따라 상대적
        - windows 9pt = 12px
        - mac 9pt = 9px
- in (인치)
    - 실제 인치 크기
    - 1인치 = 2.54cm
- cm (센티미터)
    - 실제 센티미터 크기
- mm (밀리미터)
    - 실제 밀리미터 크기
- pc (pica)
    - 1pc = 1/6 inch

#### 상대 길이 단위

- 시준이 되는 값이 따라 크기가 변함
- 부모 요소나 다른 속성을 기준으로 크기가 결정
- % (퍼센트)
    - 부모 요소를 기준으로 비율을 설정
- em
    - 현재 요소의 font-size를 기준으로 크기를 결정
    - 상위 요소의 폰트 크기에 따라 영향을 받음
    - 소수점 3자리까지 표현 가능
    - 브라우저의 기본 글꼴 크기(default)가 16px이므로 기본적으로 1em = 16px, 
    부모 요소에서 font-size를 변경했다면, 그에 따라 1em의 크기도 변화
- rem
    - 루트 요소의 폰트 크기를 기준으로 크기를 결정
        - _루트 요소(root element): HTML 문서에서 가장 최상위에 위치한 `<html>`태그_
    - 상위 요소와 상관없이 항상 일정한 크기를 유지
- vw (viewport width)
    - viewport(브라우저 창)의 너비를 기준으로 비율을 설정
    - 1vw = viewport width의 1%

---

### 색상

- 속성명: `color`
- 속성값: 색상 이름, HEX 색상 코드, RGB, RGBA, HSL, HSLA

#### 색상 이름

- CSS에서 미리 정의된 색상들의 이름을 사용하여 색상을 지정하는 방법
- 예: `red`, `green`, `blue`
- `transparent`는 투명을 나타냄
- 코드가 간단하고 읽기 쉽지만, 색상을 세밀하게 조정할 수 없음
- 예: `color: red`

#### HEX 색상 코드

- `#`기호 뒤에 6자리의 16진수로 색상을 표현
- 첫 두자리는 빨간색, 그 다음 두자리는 초록색, 마지막 두자리는 파란색을 나타냄
- 예: 초록색은 `color: #00FF00`

#### RGB

- RGB는 각각 Red, Green, Blue를 뜻함
- 각각의 비율을 0~255의 값으로 지정
- 각 숫자는 해당 색상의 강도를 나타냄
- 예: 빨간색은 `color: rgb(255,0,0)`

#### RGBA

- RGBA는 RGB에 알파(Alpha)값을 추가한 것
- 알파(Alpha)값은 투명도(Opacity)를 나타냄
- 알파 값은 0(완전 투명)에서 1(불투명) 사이의 값으로 설정, 소수점 표기
- 색상의 투명도를 조절할 수 있어서, 요소가 배경에 얼마나 투명하게 보일지를 설정 가능
- 예: 반투명한 검은색 `color: rgba(0,0,0,0.5)`

#### HSL

- HSL은 각각 Hue(색조), Saturation(채도), Lightness(명도)를 뜻함
- 색조(Hue)는 0~360까지의 각도로 색상의 종류를 정의(빨간색 0도, 초록색120도, 파란색 240도)
- 채도(Saturation)는 색상의 선명도를 0%(회색)에서 100%(가장 선명한 색)로 나타냄
- 명도(Lightness)는 색상의 밝기를 0%(검은색)에서 100%(흰색)로 나타냄
- 예: 초록색 `color: hsl(120, 100%, 50%)`

#### HSLA

- HSLA는 HSL에 알파(Alpha)값을 추가한 것
- 알파(Alpha)값은 투명도(Opacity)를 나타냄
- 예: 반투명한 파란색 `color: hsla(240, 100%, 50%, 0.5)`

---

### background

- 요소의 배경을 설정하는 데 사용
- 여러 개의 세부 속성을 결합하여 배경을 지정

#### background-color

- 배경색을 설정
- 기본값: transparent
- 예: `background-color: blue`

#### background-image

- 배경으로 이미지를 설정
- url의 경로는 절대 경로, 상대 경로 모두 사용 가능
- 예: `background-image: url('image.jpg')`

#### background-repeat

- 배경 이미지의 반복 여부와 방향을 설정
- 기본값: repeat
- 속성값
    - repeat: 기본값, x,y축 방향으로 모두 반복
    - repeat-x: x축 방향으로 반복
    - repeat-y: y축 방향으로 반복
    - no-repeat: 이미지를 반복하지 않음

#### background-position

- 배경 이미지의 위치를 설정
- 기본값: 0% 0% (왼쪽 상단)
- x,y축으로부터의 위치를 지정
- 한쪽만 지정된다면 나머지는 중앙 값(center)으로 적용
- 속성값
    - %: 기준으로부터 %만큼 상대적으로 떨어진 위치 설정
    - px: 기준으로부터 px만큼 절대적으로 떨어진 위치 설정
    - 키워드
        - x축: left, center, right
        - y축: top, center, bottom

#### background-attachment

- 화면을 스크롤(scroll)할 때 배경 이미지의 움직임 여부 설정
- 기본값: scroll
- 속성값
    - scroll: 기본값
        - 배경 이미지는 요소 자체를 기준으로 고정
        - 스크롤 시 배경도 함께 이동
    - fixed
        - 배경 이미지는 뷰포트를 기준으로 고정
        - 스크롤 시 배경이 고정
    - local
        - 배경 이미지는 요소의 내용을 기준으로 고정
        - 스크롤 시 내용과 함께 스크롤

#### background-size

- 배경 이미지의 크기를 설정
- 기본값: auto
- 속성값
    - auto: 기본 값, 기본 크기, 이미지 크기 그대로
    - cover: 요소를 완전히 덮도록 크기를 조정
    - contain: 이미지가 요소 내부에 맞도록 크기를 조정
    - 고정된 픽셀(px)값, 백분율도 지정 가능

#### background-origin

- 배경 이미지의 위치가 기준으로 삼을 영역을 설정
- 기본값: padding-box
- 속성값
    - border-box: 경계 박스를 기준
    - padding-box: 패딩 박스를 기준
    - content-box: 콘텐츠 박스를 기준

#### background-clip

- 배경이 어느 영역에 그려질지 설정
- 기본값: border-box
- 속성값
    - border-box: 경계 박스 내에 그려짐
    - padding-box: 패딩 박스 내에 그려짐
    - content-box: 콘텐츠 박스 내에 그려짐

#### 축약

- background 속성들을 하나의 줄에 결합하여 사용 가능
- 예: `background: #f00 url('image.jpg') no-repeat center center fixed`
    - 배경색: 빨간색, `image.jpg`사용, 반복 없음, 가운데 배치, 스크롤 시 배경 고정

---

### boxmodel

- 각 HTML 요소는 사각형의 박스 형태로 만들어짐
- 박스는 4개의 주요 영역으로 나눠짐
- 콘텐츠 영역 (Content)
    - 요소의 실제 내용을 포함하는 영역
    - 크기는 내용의 너비 및 높이를 나타냄
- 내부 여백 (Padding)
    - 콘텐츠와 테두리 사이의 영역
    - content 영역의 배경, 색, 이미지가 패딩 영역까지 영향을 미침
- 테두리 (Border)
    - 콘텐츠 영역을 감싸는 테두리
- 외부 여백 (Margin)
    - 테두리 바깥의 영역
    - 요소와 다른 요소 사이의 간격

---

### border

- 요소의 테두리를 설정
- 네 가지 방향(위 top, 오른쪽 right, 아래 bottom, 왼쪽 left)에 각각 다르게 설정 가능

#### border-width

- 테두리의 두께를 설정
- 기본값: medium
- 속성값
    - 단위: px, em, rem, % 등
    - 키워드
        - thin: 가장 얇은 테두리, 일반적으로 1px
        - medium: 기본적인 테두리 두께, 일반적으로 3px
        - thick: 두꺼운 테두리, 일반적으로 5px
- 축약: `border-width: [top] [right] [bottom] [left]`
- 예: `border-width: 2px`, `border-top-width: thin`

#### border-style

- 테두리의 모양을 설정
- 기본값: none
- 속성값
    - none: 테두리 없음
    - solid: 실선
    - dashed: 점선
    - dotted: 점선
    - double: 이중선
    - groove: 홈이 파인 선 (3D 효과)
    - ridge: 솟아있는 선 (3D 효과)
    - inset: 안쪽 그림자 효과 (3D 효과)
    - outset: 바깥쪽 그림자 효과 (3D 효과)
    - hidden: 테두리가 숨겨짐 (특히 테이블에서 사용)
- 축약: `border-style: [top] [right] [bottom] [left]`

#### border-color

- 테두리의 색상을 설정
- 기본값: currentcolor
- 속성값
    - 색상 이름, hex, rgb, rgba 등 CSS에서 사용되는 일반적인 색상 값
- 축약: `border-color: [top] [right] [bottom] [left]`

#### 축약

- border 속성들을 하나의 줄에 결합하여 사용 가능
- `border: [-width] [-style] [-color]`
- 예: `border: 2px solid, red`
    - 두께 2px, 실선, 빨간색 테두리

#### 이외의 border속성들도 존재

---

### padding

- border와 content 사이의 여백
- 네 가지 방향(위 top, 오른쪽 right, 아래 bottom, 왼쪽 left)에 각각 다르게 설정 가능
- 기본값: 0
- 속성값
    - px, em 등: 고정값으로 지정
    - %: 요소의 width에 상대적인 크기를 지정
- padding-top: content 영역의 위쪽 여백을 지정
- padding-right: content 영역의 오른쪽 여백을 지정
- padding-bottom: content 영역의 아래쪽 여백을 지정
- padding-left: content 영역의 왼쪽 여백을 지정
- 축약: `padding: [-top] [-right] [-bottom] [-left]`
    - 상하, 좌우 영역의 값이 같을 때 하나로 합쳐서 적용 가능
    - 예
        - padding: 10px; /* 상, 하, 좌, 우 모두 10px */
        - padding: 10px 20px; /* 상/하: 10px, 좌/우: 20px */
        - padding: 10px 20px 30px; /* 상: 10px, 좌/우: 20px, 하: 30px */
        - padding: 10px 20px 30px 40px; /* 상: 10px, 우: 20px, 하: 30px, 좌: 40px */

---

### margin

- 요소 주변의 외부 여백
- 요소와 다른 요소 사이에 공간을 추가하거나 조정 가능
- 네 가지 방향(위 top, 오른쪽 right, 아래 bottom, 왼쪽 left)에 각각 다르게 설정 가능
- 기본값: 0
- 속성값
    - px, em 등: 고정값으로 지정
    - %: 요소의 width에 상대적인 크기를 지정
    - auto: 브라우저에 의해 계산된 값이 적용
        - 좌우의 margin이 모두 auto로 적용 되었다면, 
        브라우저는 요소가 가질 수 있는 가로 영역에서 자신의 width를 제외한 나머지 여백의 크기에 대해
        균등 분할하여 적용
- margin-top border 영역의 위쪽 여백을 지정
- margin-right border 영역의 오른쪽 여백을 지정
- margin-bottom border 영역의 아래쪽 여백을 지정
- margin-left border 영역의 왼쪽 여백을 지정
- 축약: `margin: [-top] [-right] [-bottom] [-left]`
    - 상하, 좌우 영역의 값이 같을 때 하나로 합쳐서 적용 가능

#### margin collapse

- 마진 병합
- 인접한 두 개 이상의 수직 방향 박스의 마진이 하나로 합쳐지는 것을 의미
- 마진 병합은 수직 방향으로만 이루어짐
- 마진 병합은 마진이 반드시 맞닿아야 발생
- 마진 병합 시 둘 중 더 큰 값이 적용
- 두 요소가 상하로 인접한 경우
    - 위 요소의 하단 마진과 아래 요소의 상단 마진의 병합이 일어남
    - 부모 요소의 상단 마진과 첫 번째 자식 요소의 상단 마진 병합
    - 부모 요소의 하단 마진과 마지막 자식 요소의 하단 마진 병합
- 내용이 없는 빈 요소의 경우
    - 해당 요소의 상단 마진과 하단 마진의 병합이 일어남
- 마진에 음수 값을 사용할 수 있으며, 이를 통해 요소를 서로 겹치게 만들 수 있음

---

### padding과 margin 비교

| |양수값|음수값|auto|단위|
|---|---|---|---|---|
|margin|o|o|o|px, %, ...|
|padding|o|x|x|px, %, ...|

- margin은 음수 값을 통해 요소를 서로 겹치게 만들 수 있음
- margin은 좌우auto를 통해 수평 중앙 정렬 가능
- %단위를 사용할 때
    - margin, padding 모두 상하좌우에 관계없이 요소의 width 값을 기준으로 값이 결정 됨

---

### width

- 요소의 너비를 설정
- width는 요소의 콘텐츠 영역에만 적용
- width 속성은 인라인 레벨 요소를 제외한 모든 요소에 적용
- 기본값: 0
- 속성값
    - auto: 브라우저에 의해 계산된 값이 적용, 요소의 레벨 기본 특성에 따라 다르게 동작
    - px, em 등: 고정값으로 지정
    - %: 부모 요소의 width에 상대적인 크기를 지정
- width는 content 영역의 너비를 제어할 때 사용하는데, 이때 auto가 아닌 특정한 값을 지정하여 사용하면
    그 크기는 boxmodel 영역에서 margin 영역을 제외한 모든 영역에 대해 영향을 받음
- 예
    ```
    <div class="box"> box </div>

    .box {
    width: 100px;
    padding: 20px;
    border: 10px solid black;
    }
    ```

    - 요소의 총 가로 크기는 160px
    - `content의 width 100px + padding 좌우(20px*2) + border 좌우(10px*2) = 160px`

    <br>
    
    ```
    <div class="parent">
    <div class="child">
        child
    </div>
    </div>
    
    .parent {
    width: 300px;
    border: 20px solid red;
    }
    .child {
    width: 50%;
    padding: 20px;
    border: 10px solid black;
    }
    ```

    - 요소의 총 가로 크기는 210px
    - `content의 width 150px + padding 좌우(20px*2) + border 좌우(10px*2) = 210px`

<br>

- 부모가 인라인 레벨 요소일 때, 자식(블록 요소)이 width 값에 %를 가지면, 가장 가까운 블록 레벨인 조상의 width를 기준으로 계산
- 만일 최상단까지 블록 레벨 요소가 없으면 body를 기준으로 계산

---

### height

- 요소의 높이를 설정
- height는 요소의 콘텐츠 영역에만 적용
- 기본값: 0
- 속성값
    - auto: 브라우저에 의해 계산된 값이 적용, content 영역의 내용만큼 높이를 가짐
    - px, em 등: 고정값으로 지정
    - %: 부모 요소에 대한 상대적 높이를 설정
        - 단, 부모 요소가 명시적으로 height 값이 있어야 함
- height는 content 영역의 높이를 제어할 때 사용하는데, 이때 auto가 아닌 특정한 값을 지정하여 사용하면, 
    width 속성과 마찬가지로 boxmodel 영역에서 margin 영역을 제외한 모든 영역에 대해 영향을 받음
- 예
    ```
    <div class="box"> box </div>

    .box {
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 15px solid black;
    }
    ```
    - 요소의 총 세로 크기는 150px
    - `content의 height 100px + padding 상하(10px*2) + border 상하(15px*2) = 150px`

    <br>

    ```
    <div class="parent">
    <div class="child">
        child
    </div>
    </div>
    
    .parent {
    width: 200px;
    border: 10px solid black;
    }
    .child {
    height: 50%;
    background: red;
    }
    ```
    - 요소의 총 세로 크기는 `height:auto`일 때와 같음
        - 부모 요소가 명시적으로 height 값이 있어야 하기 때문

---

### typography

- 웹 페이지에서 텍스트의 스타일을 설정하는 중요한 요소

#### typography의 구조

- em: 폰트의 전체 높이
- ex: `=x-height`, 해당 폰트의 영문 소문자 x의 높이
- baseline
    - 텍스트가 수평으로 배치되는 기준선
    - 소문자 x를 기준으로 하단의 라인
    - 글자들의 기본 위치
    - 대부분의 글꼴에서 소문자가 기준선 위에 놓임
- descender
    - 소문자 x의 하단 라인 아래로 내려간 부분
    - 기준선 아래로 내려간 부분
    - 소문자 g, j, p, q, y 등에서 볼 수 있음
- ascender
    - 소문자 x의 상단 라인 위로 올라간 부분
    - 기준선 위로 올라간 부분
    - 소문자 b, d, f, h, k, l, t 등에서 볼 수 있음

---

### font-family

- 텍스트의 글꼴을 지정하는 속성
- 여러 글꼴을 쉼표로 구분하여 나열 가능
- 브라우저가 첫 번째 글꼴을 사용할 수 없으면 그 다음 글꼴로 자동으로 넘어감
- 기본적으로 대표 폰트를 선언, 특정 폰트가 필요한 부분에서 재정의
- 축약: `font-family: family-name | generic-family ( | initial | inherit )`
    - `font-family`: 사용할 폰트의 이름
        - 쉼표로 구분하여 여러개 선언 가능
        - 먼저 선언된 순서대로 우선순위가 결정
        - 이름 중간에 공백이 있거나, 한글일 경우 홑따옴표로 묶어서 선언
    - `generic-family`: 지정된 글꼴을 사용할 수 없을 경우를 대비해 대체할 수 있는 폰트
        - `font-family` 속성의 가장 마지막에 선언
        - 키워드이므로 따옴표 등의 인용부호로 묶지 않음
        - 예
            - serif: 삐침이 있는 글꼴
            - sans-serif: 삐침이 없는 글꼴
                _sans: 프랑스어로 `없음`을 뜻함_

---

### line-height

- 텍스트의 행 간격을 조정하는 속성
- 텍스트가 포함된 요소의 각 행(라인) 간의 수직적인 간격을 설정
- line-box라고도 하며, 타이포그래피의 구조에서 `em 박스 + 상/하단의 여백`
- 기본값: normal
- 축약: `line-height: normal | number | length | initial | inherit`
    - `normal`: 기본값
        - 브라우저의 기본 스타일에 따라 자동으로 설정
        - 글꼴의 크기에 비례한 값을 가짐
        - 보통 텍스트의 글꼴 크기의 약 1.2배
    - `number`: font-size를 기준으로 설정한 숫자만큼 배율로 적용
    - `length`: px, em 등 고정값으로 지정
    - `%`: font-size를 기준으로 설정한 퍼센트만큼 배율로 적용
    - `number`와 `%`의 차이
        - `number`: 부모 요소의 숫자 값이 그대로 상속
        - `%`: 부모 요소에서 %에 의해 이미 계산된 px값이 상속
        - 예
            ```
            body { font-size: 20px; line-height: 2; }    /* line-height = 40px; */
            p { font-size: 10px; }                       /* line-height = 20px; */

            body { font-size: 20px; line-height: 200%; }    /* line-height = 40px; */
            p { font-size: 10px; }                          /* line-height = 40px; */
            ```

---

### font-size

- 텍스트의 크기를 지정하는 속성
- 기본 값: medium
- 축약: `font-size: keyword | length | initial | inherit`
- 속성 값
    - `keyword`
        - `absolute size`
            - 기본 값인 medium에 대한 상대적인 크기
            - 브라우저마다 사이즈가 다르게 정의
            - `xx-small`, `x-small`, `small`
            - `medium`: 기본 값
            - `large`, `x-large`, `xx-large`
        - `relative size`
            - 부모 요소의 fon-size에 대해 상대적
            - `smaller`
                - 부모 요소의 크기보다 작은 크기
                - 상대적인 크기를 줄이는 데 유용
                - 0.8배
            - `larger`
                - 부모 요소의 크기보다 큰 크기
                - 상대적인 크기를 늘이는 데 유용
                - 1.2배
    - `length`: px, em 등 고정값으로 지정
        - `px`: 화면의 해상도와 관계없이 고정된 크기
        - `em`: 부모 요소의 font-size에 em 값을 곱한 크기
        - `rem`: 루트의 font-size에 rem 값을 곱한 크기
    - `%`: 부모 요소의 font-size를 기준으로 설정한 퍼센트만큼 적용
    - `viewport unit`: 뷰포트를 기준으로 font-size를 지정
        - `vw`: 화면 너비(width)의 백분율
        - `vh`: 화면 높이(height)의 백분율

---

### font-weight

- 텍스트의 굵기를 지정하는 속성
- 기본 값: normal
- 축약: `font-weight: normal | bold | bolder | lighter | number | initial | inherit`
- 속성 값:
    - number
        - 100 200 300 400 500 600 700 800 900
        - 클수록 더 두껍게 표현
    - `normal`: 기본 값 (400)
    - `bold`: 굵게 (700)
    - `bolder`: 부모 요소 보다 두껍게 표현
    - `lighter`: 부모 요소 보다 얇게 표현
- 숫자를 이용한 font-weight는 폰트 자체에서 지원을 해야 표현 가능
- `normal`과 `bold`만 지원하는 폰트의 경우 100~500: `normal`, 600~900: `bold`
- 디바이스별로 다르게 표현될 수도 있음

---

### font-style

- 텍스트의 스타일을 지정하는 속성
- 기본 값: normal
- 축약: `font-style: normal | italic | oblique | initial | inherit`
- 속성 값
    - `normal`: 기본 값
    - `italic`: 글자 기울기가 오른쪽으로 기울어짐
    - `oblique`
        - 비스듬하게 기울인 스타일
        - 이탤릭체와 비슷하지만, 폰트의 원래 형태에 따라 다르게 보임
        - 기울기 지정 가능
            - -90도 ~ 90도
            - 기본값 14도
            - `font-style oblique 10deg`: 10도 기울임

---

### font-variant

- 텍스트의 서체 변형을 지정하는 속성
- 이 속성을 이용해 소문자를 작은 대문자로 변환 가능
- 변환된 대문자는 실제 대문자 사이즈 보다 작은 사이즈
- 대소문자 변환이므로 한글에는 적용되지 않음
- 기본 값: normal
- 축약: `font-variant: normal | small-caps | initial | inherit`
- 속성 값
    - `normal`: 기본 값, 어떤 변형도 적용하지 않음
    - `small-caps`: 소문자를 소문자 크기의 대문자로 변형

---

### font

- 여러 가지 폰트 관련 속성의 축약형 속성
- 속성마다 선언 순서를 지켜야 함
- `font: font-style font-variant font-weight font-size/line-height font-family | initial | inherit`
- `font` 속성에서는 `font-size`와 `font-family`를 반드시 지정해야 함
- `line-height`는 `/`뒤에 작성, 선택적으로 지정 가능

---

### webfont

- 웹페이지에서 글꼴을 지정할 때 사용되는 기술
- 서버나 클라이언트에 저장된 글꼴을 웹페이지에 적용할 수 있게 함
- 글꼴을 직접 웹페이지에 포함시키거나 웹에서 다운로드하여 사용하는 방식
- 사용자의 컴퓨터에 특정 글꼴이 없더라도 웹 페이지에서 해당 글꼴을 제대로 표시 가능

#### @font-face

- 웹페이지에서 사용할 폰트를 외부 파일로부터 사용자의 로컬 환경으로 다운로드하여 사용
- 기본 값: 없음
- 속성 값
    - `font-family`: 글꼴의 이름을 지정 (필수)
    - `src`: 다운로드 받을 글꼴의 경로(url) (필수)
    - `font-style`: 글꼴의 스타일 지정
        - 기본 값: normal
    - `font-weight`: 글꼴의 굵기 지정
        - 기본 값: normal
- 예
    ```
    @font-face {
    font-family: webNanumGothic; /* 사용자 지정 웹 폰트명 */
    src: url(NanumGothic.eot); /* 적용 될 웹 폰트의 경로 */
    font-weight: bold; /* 필요에 따라 지정 */
    font-style: italic; /* 필요에 따라 지정 */
    }

    body {
        font-family: webNanumGothic;
    }
    ```

---

### vertical-align

- 인라인 또는 인라인-블록 요소를 기준으로 다른 요소들과의 수직 정렬을 제어
- 속성이 적용되는 요소들
    - inline 요소: `<span>`, `<a>`, `<img>` 등
    - inline-block 요소: `<button>`, `<input>` 등
- 기본 값: baseline
- 축약: `vertical-align: keyword | length | percent | initial | inherit`
- 속성 값
    - keyword
        - baseline(기본 값): 요소의 텍스트 기준선(baseline)을 기준으로 정렬
        - top: 요소의 상단을 부모 요소의 상단에 맞춤
        - middle: 요소의 수직 중앙을 부모 요소의 수직 중앙에 맞춤
        - bottom: 요소의 하단을 부모 요소의 하단에 맞춤
        - super: 텍스트의 상위 첨자처럼 배치
        - sub: 텍스트의 하위 첨자처럼 배치
    - length
        - baseline을 기준으로 이동
        - 요소를 지정한 길이만큼 올리거나 내림
        - 음수 값 사용 가능
        - 양수 값은 요소를 위로 이동
        - 음수 값은 요소를 아래로 이동
    - %
        - line-height를 기준으로 내에서 이동
        - 음수 값 사용 가능

---

### text-align

- 요소 내의 텍스트나 인라인 요소들을 수평 방향으로 어떻게 정렬할지 지정
- 기본 값: left (Right to Left 언어일 경우는 right)
- 축약: `text-align: left | right | center | justify | initial | inherit`
- 속성 값
    - left: 텍스트를 왼쪽에 정렬
    - right: 텍스트를 오른쪽에 정렬
    - center: 텍스트를 수평 중앙에 정렬
    - justify: 텍스트를 양쪽 끝에 맞게 정렬
        - 마지막 라인은 정렬하지 않음
    - start: 텍스트 정렬을 문서의 시작 부분에 맞춤
    - end: 텍스트 정렬을 문서의 끝 부분에 맞춤

---

### text-indent

- 블록 요소 내의 첫 번째 줄 텍스트를 들여쓰기
- 기본 값: 0
- 축약: `text-indent: length | initial | inherit`
- 속성 값
    - length: px, em 등 고정 값으로 지정, 음수로 내어쓰기 가능
    - %: 부모 요소의 width를 기준으로 지정

---

### text-decoration

- 텍스트의 장식 스타일을 설정하는 속성
- 주로 밑줄, 취소선, 강조선 등을 추가하는 데 사용
- 기본 값: none currentColor solid
- 측약: `text-decoration: text-decoration-line text-decoration-color text-decoration-style | initial | inherit`
- 속성 값
    - `text-decoration-line`: 텍스트 장식의 종류를 지정
        - none: 텍스트 장식을 생성하지 않음 (기본 값)
        - underline: 텍스트에 밑줄을 추가
        - overline: 텍스트에 윗줄을 추가
        - line-through: 텍스트에 중간을 지나는 취소선을 추가
    - `text-decoration-color`: 텍스트 장식의 색상을 설정
        - 기본 값: currentColor
        - 색생 값을 사용하여 원하는 색상을 지정 가능
    - `text-decoration-style`: 텍스트 장식의 스타일을 설정
        - solid: 한줄 (기본 값)
        - double: 이중선
        - dotted: 점선
        - dashed: 파선
        - wavy: 물결

---