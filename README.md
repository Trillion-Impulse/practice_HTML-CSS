# how to use CSS
***

## CSS

- Cascading Style Sheets
- Cascading: 여러 스타일 규칙이 있을 때, 우선 순위를 통해 스타일이 적용되는 방식
- 웹 페이지의 스타일과 레이아웃을 정의하는 언어
- HTML이 정의한 페이지의 구조에 색상, 글꼴, 간격, 배치 등 시각적 요소를 추가하여 웹 페이지의 디자인을 담당

## Syntax

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

### HTML 속성과 CSS 속성

|구분|HTML 속성|CSS 속성|
|-|-|-|
|목적|HTML 요소의 기능과 동작을 설정|HTML 요소의 스타일을 설정|
|위치|HTML 태그 내|CSS 파일 또는 `<style>` 태그 내 또는 인라인|
|적용 대상|HTML 요소의 구조적 속성을 정의|HTML 요소의 디자인 및 레이아웃을 설정|
- HTML 속성은 Attribute
- CSS 속성은 Property


### 주석

```
/* 주석 */
```
- `/*`로 시작, `*/`로 끝남

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

## 선택자 (Selector)

- 스타일을 적용할 HTML 요소를 선택하는 역할

### 요소 선택자 (Element Selector)

- 특정 HTML 태그에 스타일을 적용
- 태그 선택자라고도 함
- 문서 내에 선택자에 해당하는 모든 요소에 스타일 규칙이 적용
```
p {
    color: blue;
}
```

### 그룹화 선택자 (Grouping Selector)

- 여러 선택자를 한 번에 묶어서 스타일을 적용 가능
- `,`쉼표로 구분
```
h1, h2, h3 {
    color: green;
}
```

### 전체 선택자 (Universal Selector)

- 모든 HTML 요소를 선택하는 선택자
- `*`asterisk 기호 사용
```
* {
    color: red;
}
```

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

### 아이디 선택자 (Id Selector)

- 특정 ID를 가진 요소에 스타일을 적용
- `#`을 사용하여 아이디를 선택
- ID는 문서 내에서 유일하므로 ID 선택자로 규칙을 적용할 수 있는 요소는 단 하나
```
#bar {
    background-color: yellow;
}
```
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

### 부분 속성값으로 선택

- `[class~="bar"]`: class 속성의 값이 공백으로 구분한 "bar" 단어가 포함되는 요소 선택
- `[class^="bar"]`: class 속성의 값이 "bar"로 시작하는 요소 선택
- `[class$="bar"]`: class 속성의 값이 "bar"로 끝나는 요소 선택
- `[class*="bar"]`: class 속성의 값에 "bar"문자가 포함되는 요소 선택

### 선택자의 조합

- 요소와 클래스의 조합
    - `p.bar{...}`
- 다중 클래스
    - `.foo.bar{...}`
- 아이디와 클래스의 조합
    - `#foo.bar{...}`

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

### 캐스케이딩

- Cascading
- 스타일이 적용되는 과정에서 우선순위를 결정하는 중요한 규칙
- CSS 규칙이 적용되는 순서
    1. 중요도(`!important`)
    2. 구체성 점수
    3. 선언 순서
        - 동일한 구체성을 가진 규칙이 여러개 있을 경우, 나중에 선언된 규칙이 우선 적용

### 선택자 레퍼런스

- [https://www.w3schools.com](https://www.w3schools.com/cssref/css_selectors.php)


## 속성

- HTML 요소의 스타일을 정의
- `속성명: 값` 형태로 작성

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

### CSS reference

- [https://www.w3.org](https://www.w3.org)
- [https://www.w3schools.com](https://www.w3schools.com)
- [https://developer.mozilla.org](https://developer.mozilla.org)

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

### background

- 요소의 배경을 설정하는 데 사용
- 여러 개의 세부 속성을 결합하여 배경을 지정