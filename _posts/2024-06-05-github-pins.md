---
title: Github pins 커스텀하기
categories: [Study, Github]
tags: [github, pin, github-stats-box, lang-box]
---

# 개념
## pin
- 다른 사용자에게 내 작업 중 가장 보여주고 싶은 것을 빠르게 보여주기 위해 프로필에 gist나 repository를 고정하는 기능을 말한다.
- 소유한 Public repository만 고정 가능하다.

## gist
- 타인에게 코드 블럭을 간단하게 공유할 수 있는 기능이다.
- 모든 gist는 git repository이기 때문에 clone과 fork가 가능하다.
- Public gist와 Private gist 두 종류의 gist를 만들 수 있다. (repository의 puvlic과 private와 유사하다.)

## github-stats-box
- 사용자의 github stats의 통계를 보여준다.
- MIT license

## lang-box
- 사용자가 최근 작업한 프로그래밍 언어 및 마크업 언어 등의 통계를 보여준다.
- MIT license

<br/>
<br/>
<br/>

# Setting
## Github Profile
1. username과 동일한 이름의 repository를 생성한다.
    - readme.md 파일 생성을 체크하는 것을 추천한다. 어차피 생성해야 한다.
    ![repo_create](/assets/img/post_img/pin/repo_create.png){.normal}

    <br/>

2. repository 생성 후 overview 탭 화면
    ![overview](/assets/img/post_img/pin/overview-start.png){.normal}

<br/>

## github-stats-box
1. [github-stats-box](https://github.com/LellowMellow/github-stats-box)로 이동하여 해당 repository를 fork한다.
    ![fork](/assets/img/post_img/pin/fork.png){.normal}
    ![fork](/assets/img/post_img/pin/fork-2.png){.normal}
    <br/>
2. Token 발급을 위해 [github token](https://github.com/settings/tokens/new)로 이동한다.
    ![token](/assets/img/post_img/pin/gist-token-repo-gist-Generate-token.png){.normal}
    - Note의 이름은 사용자가 알아보기 쉽게 설정하면 된다.
    - Select scopes의 경우, 해당 token을 fork 받은 repository의 gist에서 활용할 것이기 때문에 repo와 gist를 선택해야 한다.
    - 발급 시 아래의 화면으로 페이지가 넘어가는데, 검은색으로 줄이 쳐져 있는 곳이 token이다. 토큰 값은 페이지를 벗어나면 찾을 수 없으니 꼭 어딘가에 남겨두는 것이 좋다.
    ![token](/assets/img/post_img/pin/token-success.png){.normal}
    <br/>
3. [gist](https://gist.github.com/)에서 gist를 생성한다.
    ![gist](/assets/img/post_img/pin/gist-create.png){.normal}
