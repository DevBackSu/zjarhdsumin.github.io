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

    ![Desktop View](/assets/img/post_img/searchconsole/file_st.png){:width="300" height="600" .left}
    
    > html 파일을 통해 소유권을 검사하기 때문에 삭제하면 안 됨



5. github에서 push 완료를 확인 한 후 위 `(3번)` 이미지의 확인 버튼을 누르면 아래의 팝업이 뜸

    ![Desktop View](/assets/img/post_img/searchconsole/check_html.png){:width="600" height="500"}

    **[속성으로 이동]** 버튼 클릭 시 아래의 화면으로 이동됨

    ![Desktop View](/assets/img/post_img/searchconsole/searchconsole_main.png){:width="700" height="700"}



6. gemfile 수정 후 ruby prompt에서 bundle install과 jekyll serve을 순차적으로 입력
    (참고한 블로그에서는 jekyll-sitemap 추가 후 install 했을 때 로그에 추가한 내용이 찍히는데 필자는 찍히지 않음. 그래도 이어서 진행함)

    ![Desktop View](/assets/img/post_img/searchconsole/gemfile_sitemap.png){:width="400" height="400"}



7. 이후 http://localhost:4000/sitemap.xml 에 접속하면 sitemap.xml 파일 내용 확인 가능. 이 xml 파일을 복사해서 Gemfile의 위치에 동일한 이름의 파일을 생성한 후 붙여 넣기 한 후 같은 위치에 robots.txt를 넣기 (내 경우, robots.txt가 assets 폴더 내에 있어서 아래의 경로로 이동시킴)

    | ![Desktop View](/assets/img/post_img/searchconsole/sitemap.png) | ![Desktop View](/assets/img/post_img/searchconsole/robots.png)  |
    | :--------------------------- | :--------------- |
    | sitemap.xml과 robots.txt 위치 |  robots.txt 내용  |

    robots.txt이란?[^footnote]
    : 검색 로봇에게 웹 페이지 접근을 허용 및 제한하는 국제 권고안으로, 크롤링해서는 안 되는 사이트 내 URL이나 디렉터리를 검색 엔진에게 알려주는 텍스트 파일의 이름. 반드시 사이트의 루트 디렉터리에 위치해야 하며 텍스트 파일로 접근이 가능해야 함

    | robots.txt 변수명 | 설명 |
    | :------------------- | :------------------------------------------- |
    | User-agent | robots.txt에서 지정하는 크롤링 규칙이 적용되어야 할 크롤러를 지정. *은 모든 검색 엔진 로봇의 접근 허용을 뜻함. (크롤러명 : 구글 (Googlebot) / 네이버 (Yeti) / 다음 (Daum) 등) |
    | :------------------- | :------------------------------------------- |
    | Disallow | 크롤링을 제한할 경로 |
    | :------------------- | :------------------------------------------- |
    | Allow | 크롤링을 허용하는 경로 |
    | :------------------- | :------------------------------------------- |
    | Sitemap | sitemap 경로 |



8. 7번의 수정 내용을 github에 올린 `(add -> commit -> push)` 후 Google Search Console의 sitemap 으로 들어가 사이트맵 `sitemap 파일명` 을 추가

    ![Desktop View](/assets/img/post_img/searchconsole/plus_site.png){:width="800" height="400"}



9. git push가 잘 됐다면 제출 버튼 클릭 시 아래의 팝업이 뜨고 제출된 사이트맵 목록도 확인 가능함. 위 설정 완료 시 7일 이내에 검색 엔진에 노출됨

    ![Desktop View](/assets/img/post_img/searchconsole/success_sitemap.png){:width="800" height="500"}
    ![Desktop View](/assets/img/post_img/searchconsole/sitemap_list.png){:width="800" height="400"}




---


# Err List

## 24.05.24 Problem

<figure class="half"> 
    <a href="link"><img src="/assets/img/post_img/searchconsole/sitemap_err.png"></a> 
    <a href="link"><img src="/assets/img/post_img/searchconsole/err_content.png"></a> 
</figure>


서치 콘솔 설정 완료 후 일주일이 지난 어느 날 (24일), 서치 콘솔을 확인하니 위 사진의 오류가 떠 있었음.



## 시도한 방법

1. sitemap 검색해보기
    - https://(내 블로그 주소)/sitemap.xml을 검색했을 때 xml 내용이 나오는지 확인

    ![](/assets/img/post_img/searchconsole/sitemap_xml.png){: w="400" h="400"}

    -> 내용을 확인할 수 있지만 여전히 실패 상태



2. 사이트맵 삭제 후 다시 추가하기
    - 사이트맵 삭제

    ![](/assets/img/post_img/searchconsole/sitemap_delete.png){ : w="400" h="300"}

    - 사이트맵 추가

    ![](/assets/img/post_img/searchconsole/sitemap_plus.png){ : w="300" h="200"}

    -> 여전히 실패 상태



3. 서버 사용 불가 같은 기타 Search Console 오류
    - Github의 경우 사이트맵 인식 관련 문제가 있음.
    - 2~3개월 후에 정상 인식이 되기는 한다고 함.
    -> 모든 방법이 먹지 않으면 일단 대기를 해야 할 듯



4. robots.txt 문제
    - [Search Console 고객센터](https://support.google.com/webmasters/answer/7451001#errors){:target="_blank"} 확인하기
    - 대체로 Allow와 Disallow를 지우거나, Disallow의 경로만 지워도 해결되는 듯



5. 사이트맵에 대한 크롤링 수요가 낮음
    - 높은 품질의 컨텐츠를 제작해 수요를 높여야 함




## 해결 방법

#### Sitemap 수정

[sitemaps](https://www.xml-sitemaps.com/)에서 내 블로그 주소를 입력한 후 start 버튼 클릭 시 내 블로그의 sitemap.xml을 생성해줌

![](/assets/img/post_img/searchconsole/xml_sitemaps.png)

생성한 sitemap.xml 파일을 기존 sitemap.xml 파일이 있던 곳에 넣어 덮어쓰기

![](/assets/img/post_img/searchconsole/final_sitemap.png)



#### IF

| ![](/assets/img/post_img/searchconsole/content_err.png) | ![](/assets/img/post_img/searchconsole/page_err.png) |
| :----- | :------- |
| search console 오류 | 브라우저에서 sitemap.xml 검색 시 오류 |

만약 모두 시도한 이후에도 위와 같은 에러가 발생할 경우

- 새로 다운 받은 sitemap의 <urlset> 부분에 이전 sitemap의 <urlset>을 추가 (같은 내용은 삭제)
- sitemap 내 주석 및 엔터 부분 모두 삭제
- 수정 후 git push 했는지 확인하기

> 내 경우, 주석을 지운 후 push한 후에 sitemap이 오류를 발생시키지 않았음. 하지만 브라우저에서 sitemap을 검색했을 때는 내가 지웠던 주석이 그대로 남아있음. 아무래도 google은 무언가를 등록/수정/삭제한 이후에는 구글이 내 변경 사항을 적용할 때까지 기다려야 할 것 같음.

> 240529 | sitemap 검색 시 주석이 삭제됨. 추측 상 <urlset>을 수정한 후부터 오류가 사라진 듯.

---

### 참고

[^footnote] : 참고 - [네이버 웹마스터 가이드](https://searchadvisor.naver.com/guide/seo-basic-robots){: target="_blank"}

[Dodev님 - 초보자를 위한 Github Blog 만들기](https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-2/){: target="_blank"}

[SuperMemi님 - 나만의 블로그 만들기](https://supermemi.tistory.com/entry/%EB%82%98%EB%A7%8C%EC%9D%98-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0-Git-hub-blog-GitHubio){: target="_blank"}

[KiTFOx's Notepad님 - jekyll 테마 적용시킨 Github 블로그 로컬에서 변경사항 확인하기](https://dana3711.tistory.com/67){: target="_blank"}