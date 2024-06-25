---
title: 까먹을까봐 적어두는 CSS
categories: [Study, WEB]
tags: [study, web, css, html]
---

# 정리할 것

css는 아래 형식이고
button
button.btn
button.btn.func

html은 아래 형식인데
<button>
<button class = "btn">
<button class = "btn func">
마지막 버튼 태그 부분을 백그라운드 색을 바꾸고 싶어서 style로 !important 했는데 안 됨. -> 내가 알기로 important는 우선 순위를 가장 높게 지정하는건데 왜 안 되는건지 모르겠다. 개발자 모드에서도 우선 순위는 높아가지고 채택되어 있던데. 그래서 button.func 따로 만들어서 <button class = "func"> 함.