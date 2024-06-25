---
title: 까먹을까봐 적어두는 CSS , JS
categories: [Study, WEB]
tags: [study, web, css, html]
---

# CSS 우선순위

```css
button { ... }
button.btn { ... }
button.btn.func { ... }
```

```html
<button>버튼</button>
<button class = "btn">버튼</button>
<button class = "btn func">버튼</button>
```
## 의문점
`<button class = "btn func">` 부분만 css 수정이 필요해서 다음과 같이 수정했다.
`<button class = "btn func" style="text-align : center !important">`


important는 우선 순위를 가장 높게 지정하는 속성으로 알고 있어서 붙여주었지만 막상 실행해보니 적용되지 개발자 모드에서 채택이 되어 있음에도 적용이 되지 않았다. 속성의 문제인가 싶어서 margin 등으로 변경해도 마찬가지였다.

## 해결?
해당 버튼의 class를 만들어 `<button class = "func">` 적용했다. important는 html에서 붙이면 적용이 되지 않는건지 확인해봐야 할 것 같다.

## 참고

CSS 우선 순위

속성 뒤에 !important를 붙인 속성 > HTML에서 style을 지정한 속성 > #id로 지정한 속성 > .class로 지정한 속성 > 태그 이름으로 지정한 속성 > 상위 객체에 의해 상속된 속성

↓	↓	↓

.class { background-color : blue !important} > `<h1 style="background-color : blue">예시</h1>` > #id { background-color : blue } > .class { background-color : blue } > h1 { background-color : blue } > `<div style = "visibility : hidden"><h1></h1></div>`


자세한 설명은 아래 사이트에서 확인할 수 있다.

[데이터_박과장 님 - CSS - 스타일의 상속과 정렬](https://d-craftshop.tistory.com/98)
[ofcourse - 적용 우선순위](https://ofcourse.kr/css-course/%EC%A0%81%EC%9A%A9-%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84)


<br/>

# 새로 고침

## 페이지 새로 고침

화면 갱신 시 사용하는 함수로, window.location / location / document.location을 통해 접근이 가능하다.

```jsp
<script>
    function re(){
        document.location.reload()
    }
</script>
...
<body>
    <button onclick = "window.location.reload()">새로 고침</button>
    <button onclick = "re()">함수로 뺀 새로 고침</button>
</body>

```

## 특정 부분 페이지 새로 고침

load()를 사용해 특정 영역만 새로 고침을 할 수 있다.

```jsp
<script>
    function div_reload(){
         $("#div-id").load(window.location.href + " #div-id"); //#id 앞에 띄어쓰기 필수
    }
</script>
...
<body>
    <div id="reload_test">
        <button onclick="div_reload()">새로 고침</button>
    </div>
</body>
```
