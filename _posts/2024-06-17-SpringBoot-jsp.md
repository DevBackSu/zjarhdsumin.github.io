---
title: Spring Boot + Gradle + jsp로 웹페이지 띄우기
categories: [Study, Spring boot]
tags: [Spring Boot, gradle, jsp, jstl, web, jasper]
---

# 주요 SKILL
build tool : Gradle - groovy
language : java 22
framework : spring boot 3.2.6
dependencies : 
    - lombok
    - spring web
    - tomcat jasper
    - JSTL
    등

# jakarta

<br/>

# JSTL

<br/>

# jasper

<br/>

# Setting

## Project Structure

{% highlight text %}
main
    ㄴ java
        ㄴ com.example.mybatis
            ㄴ user
                ㄴ controller
                    ㄴ UserController.java
                ㄴ repository
                    ㄴ UserDao.java
                ㄴ service
                    ㄴ UserService.java
                    ㄴ UserServiceImpl.java
                ㄴ dto
                    ㄴ UserDto.java
            ㄴ MybatisApplication.java
    ㄴ resources
        ㄴ mapper
            ㄴ UserMapper.xml
        ㄴ aplication.properties
    ㄴ webapp
        ㄴ WEB-INF
            ㄴ views
                ㄴ admin // 관리자 웹 페이지
                ㄴ user  // 사용자 웹 페이지
{% endhighlight %}

<br/>

## build.gradle

- spring 3.0.0 이상 버전을 사용할 경우 아래의 JSTL 의존성을 추가해야 한다.

```gradle
implementation 'org.apache.tomcat.embed:tomcat-embed-jasper'
implementation 'jakarta.servlet:jakarta.servlet-api'
implementation 'jakarta.servlet.jsp.jstl:jakarta.servlet.jsp.jstl-api'
implementation 'org.glassfish.web:jakarta.servlet.jsp.jstl'
```

- spring 3.0.0 이하 버전을 사용한다면 아래의 JSTL 의존성을 추가한다.

```gradle
implementation 'org.apache.tomcat.embed:tomcat-embed-jasper'
implementation 'javax.servlet:jstl'
```

<br/>

## application.properties

- webapp/WEB-INF/views 내 jsp 파일을 사용하기 위해 View Resolver 경로를 변경한다.

```properties
spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp
```

## UserController.java

@RestController면 String 반환 시 그냥 String 값이 뜸. 다음처럼 해야 jsp가 반환됨

```java
    @GetMapping("/")
    public ModelAndView login(){
        return new ModelAndView("user/login");
    }
```

근데 @Controller면 String으로 반환해도 읽음 (ModelAndView도 jsp 반환함)

```java
    @GetMapping("/")
    public String login(){
        return "user/login";
    }
```

> 여기에다가 이유를 찾아서 적어보자.
{: .prompt-info }


<br/>

---

<br/>

# 참고

[개소왕 님 - Spring boot jsp 못 읽는 경우](https://dogcowking.tistory.com/326)

[yusub 님 - [Spring] Spring boot 3에서 jsp 설정방법](https://velog.io/@rhkdbtj/Spring-Spring-boot-3%EC%97%90%EC%84%9C-jsp-%EC%84%A4%EC%A0%95%EB%B0%A9%EB%B2%95)

[우롱차 님 - JSP를 사용하는 Spring Boot 프로젝트 생성하기](https://velog.io/@wooryung/JSP%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-Spring-Boot-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0)

[잇트루 님 - [Spring MVC] 스프링 MVC 뷰 리졸버 (View Resolver)](https://ittrue.tistory.com/237)