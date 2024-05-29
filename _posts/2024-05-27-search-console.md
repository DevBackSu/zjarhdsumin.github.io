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


1. [Google Search Console](https://search.google.com/search-console/about?hl=ko)에서 [시작하기] 버튼 클릭
![Desktop View](/assets/img/post_img/searchconsole/start.png){:width="500" height="450"}


2. 만약 로그인이 되어 있지 않은 상태라면 로그인 진행 -> 이후 search console에 등록하고 싶은 url을 입력할 수 있는 창이 뜸. 나의 경우, 내 github 블로그 `https://zjarhdsumin.github.io` 를 등록하고 싶기 때문에 다음과 같이 작성함
![Desktop View](/assets/img/post_img/searchconsole/domain.png){:width="500" height="600"}

3. 소유권 확인을 위한 절차 -> html 파일 다운로드
![Desktop View](/assets/img/post_img/searchconsole/html_file.png){:width="500" height="600"}

4. 다운로드 한 html 파일을 아래의 경로에 넣은 후 git add -> git commit -> git push 하기
![Desktop View](/assets/img/post_img/searchconsole/file_st.png){:width="500" height="800"}
> html 파일을 통해 소유권을 검사하기 때문에 삭제하면 안 됨

5. github에서 push 완료를 확인 한 후 위 `(3번)` 이미지의 확인 버튼을 누르면 아래의 팝업이 뜸
![Desktop View](/assets/img/post_img/searchconsole/check_html.png){:width="600" height="500"}
[속성으로 이동] 버튼 클릭 시 아래의 화면으로 이동됨
![Desktop View](/assets/img/post_img/searchconsole/searchconsole_main.png){:width="600" height="600"}

6. gemfile 수정 후 ruby prompt에서 bundle install과 jekyll serve을 순차적으로 입력
(참고한 블로그에서는 jekyll-sitemap 추가 후 install 했을 때 로그에 추가한 내용이 찍히는데 필자는 찍히지 않음. 그래도 이어서 진행함)
![Desktop View](/assets/img/post_img/searchconsole/gemfile_sitemap.png){:width="600" height="600" .left}
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
{: .right}