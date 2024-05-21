---
# layout : post - 기본적으로 설정되어 있는 변수
title: Spring boot 패키지 문제
date: 2024-05-20 10:20:00 +0900
categories: [project, Roomie]
tags: [spring, react, project, js, java]
---
# Project - Roomie
Spring Boot와 React.js를 사용하여 웹 프로젝트를 시작했다.

## Problem
첫 세팅 과정에서 문제가 있었는데, spring boot를 run해도 react가 api를 통해 값을 가져오지 못했다.

## 추측
#### 1. 코드 오류
우선 각 단의 코드를 살펴보았다.

- React.js

```react
import React, {useEffect, useState} from 'react';
import axios from 'axios';

function App() {
   const [d, setData] = useState('')
    useEffect(() => {
        axios.get('/api/data')
        .then(res => setData(res.data))
        .catch(err => console.log(err))
    }, []);
    return (
        <div>
            서버 반환 값 : {d}
        </div>
    );
}
export default App;

```

> 간단 설명 - axios.get()을 통해 api 호출 -> then과 catch로 성공 시 setData로 res에 전달된 반환값을 data에 set. 만약 err가 발생하면 log를 찍음

- Spring Boot

```java
package com.example.roomie.Controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.Arrays;
import java.util.List;

@RestController
public class MainController {
    @GetMapping("/api/data")
    public List<String> getData(){
        return Arrays.asList("Data1", "Data2","데이터3");
    }

    @GetMapping("/")
    public String getHomeDate() {
        return "home";
    }
}
```
> 간단 설명 : /api/data로 get 요청이 들어오면 list를 반환

api 경로가 잘못되거나 변수명이 틀리는 등의 코드 상 문제를 찾을 수 없었다.
변수를 바꿔보기도 했고, 경로를 /api/data에서 /data 로 변경해보기도 했지만 여전히 리액트는 api를 호출하지 못했다.

> 내 경우, 코드 상의 문제는 아니었다!
{: .prompt-info }



#### 2. 경로 문제

검색을 하던 중 패키지 구조 때문에 문제가 생길 수 있다는 글을 보고 내 디렉토리 구조를 확인했다.

{% highlight bash %}
...
    main
      ㄴ java
        ㄴ com.example.ProjectName
           ㄴ ProjectNameApplication
      ㄴ Controller
...
{% endhighlight %}

어째서인지 Application이 Controller와 같은 위치가 아닌데다 Controller도 위치가 이상했다. (내가 알던 위치와 달랐다.) 디렉토리 및 파일의 위치를 다음과 같이 수정했다.

{% highlight bash %}
...
    main
      ㄴ java
        ㄴ com.example.ProjectName
           ㄴ Controller
           ㄴ ProjectNameApplication
...
{% endhighlight %}

수정 후 spring boot와 react를 실행시켰더니 내가 바라던 화면을 볼 수 있었다.


#### 소감
텅 빈 백지에 '서버 반환 값 : Data1Data2데이터3' 만 둥둥 떠 있는 화면이었지만 이틀간 고민하던 문제가 해결되어서 뿌듯했다.