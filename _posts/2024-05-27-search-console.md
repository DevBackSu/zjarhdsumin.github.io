---
title: Google Search Console
categories: [Blog]
tags: [search console, github, blog]
image:
    path : /assets/img/post_img/google_logo.png
    alt : Google Search Console LOGO
---

# Google Search Console
구글 서치 콘솔

- Google에서 무료로 제공하는 서비스
- 웹 마스터 도구
- 사용자가 사이트의 구글 검색 결과 인지도를 모니터링하고 관리하며 문제를 해결하도록 도움
- 구글 검색을 통해 조회가 가능하도록 도움


---

## Github 블로그를 Search Console에 등록하는 방법


1. [Google Search Console](https://search.google.com/search-console/about?hl=ko){: target="_blank"}에서 [시작하기] 버튼 클릭
![Desktop View](/assets/img/post_img/searchconsole/start.png){:width="500" height="450"}


2. 만약 로그인이 되어 있지 않은 상태라면 로그인 진행 -> 이후 search console에 등록하고 싶은 url을 입력할 수 있는 창이 뜸. 나의 경우, 내 github 블로그 `https://zjarhdsumin.github.io` 를 등록하고 싶기 때문에 다음과 같이 작성함
![Desktop View](/assets/img/post_img/searchconsole/domain.png){:width="500" height="600"}

3. 소유권 확인을 위한 절차 -> html 파일 다운로드
![Desktop View](/assets/img/post_img/searchconsole/html_file.png){:width="500" height="600"}

4. 다운로드 한 html 파일을 아래의 경로에 넣은 후 git add -> git commit -> git push 하기
![Desktop View](/assets/img/post_img/searchconsole/file_st.png){:width="300" height="600"}
> html 파일을 통해 소유권을 검사하기 때문에 삭제하면 안 됨

5. github에서 push 완료를 확인 한 후 위 `(3번)` 이미지의 확인 버튼을 누르면 아래의 팝업이 뜸
![Desktop View](/assets/img/post_img/searchconsole/check_html.png){:width="600" height="500"}
**[속성으로 이동]** 버튼 클릭 시 아래의 화면으로 이동됨
![Desktop View](/assets/img/post_img/searchconsole/searchconsole_main.png){:width="700" height="700"}

6. gemfile 수정 후 ruby prompt에서 bundle install과 jekyll serve을 순차적으로 입력
(참고한 블로그에서는 jekyll-sitemap 추가 후 install 했을 때 로그에 추가한 내용이 찍히는데 필자는 찍히지 않음. 그래도 이어서 진행함)
![Desktop View](/assets/img/post_img/searchconsole/gemfile_sitemap.png){:width="400" height="400"}

```Gemfile
# frozen_string_literal: true

source "https://rubygems.org"

gemspec

group :test do
  gem "html-proofer", "~> 5.0"
end

gem "tzinfo", "~> 2.0"

gem "tzinfo-data", "~> 1.2024"

gem 'jekyll-sitemap'
```
> 복붙용 코드

7. 이후 http://localhost:4000/sitemap.xml 에 접속하면 sitemap.xml 파일 내용 확인 가능. 이 xml 파일을 복사해서 Gemfile의 위치에 동일한 이름의 파일을 생성한 후 붙여 넣기 한 후 같은 위치에 robots.txt를 넣기 (내 경우, robots.txt가 assets 폴더 내에 있어서 아래의 경로로 이동시킴)
| ![Desktop View](/assets/img/post_img/searchconsole/sitemap.png) | ![Desktop View](/assets/img/post_img/searchconsole/robots.png)  |
| :--------------------------- | ---------------: |
| sitemap.xml과 robots.txt 위치 |  robots.txt 내용  |

robots.txt
 : 검색 로봇에게 웹 페이지 접근을 허용 및 제한하는 국제 권고안. 반드시 사이트의 루트 디렉터리에 위치해야 하며 텍스트 파일로 접근이 가능해야 함

| User-agent | robots.txt에서 지정하는 크롤링 규칙이 적용되어야 할 크롤러를 지정. *은 모든 검색 엔진 로봇의 접근 허용을 뜻함. (크롤러명 : 구글 (Googlebot) / 네이버 (Yeti) / 다음 (Daum) 등) |
| :--------------- | :-------------- |
| Disallow | 크롤링을 제한할 경로 |
| :--------------- | ------: |
| Allow | 크롤링을 허용하는 경로 |
| :--------------- | :-------------- |
| Sitemap | sitemap 경로 |

8. 7번의 수정 내용을 github에 올린 `(add -> commit -> push)` 후 Google Search Console의 sitemap 으로 들어가 사이트맵 `sitemap 파일명` 을 추가
![Desktop View](/assets/img/post_img/searchconsole/plus_site.png){:width="800" height="400"}

9. git push가 잘 됐다면 제출 버튼 클릭 시 아래의 팝업이 뜨고 제출된 사이트맵 목록도 확인 가능함. 위 설정 완료 시 7일 이내에 검색 엔진에 노출됨
![Desktop View](/assets/img/post_img/searchconsole/success_sitemap.png){:width="800" height="500"}
![Desktop View](/assets/img/post_img/searchconsole/sitemap_list.png){:width="800" height="400"}


---


# Err List

## 24.05.24 Problem
![Desktop View](/assets/img/post_img/searchconsole/sitemap_err.png){:width="600" height="350"}
![Desktop View](/assets/img/post_img/searchconsole/err_content.png){:width="400" height="250"}
서치 콘솔 설정 완료 후 일주일이 지난 어느 날 (24일), 서치 콘솔을 확인하니 위 사진의 오류가 떠 있었음.

## 시도한 방법