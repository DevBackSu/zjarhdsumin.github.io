---
title: \[GIT] PUSH 오류
categories: [Study, Github]
tags: [git, github, error, push]
pin: false
---

# ERROR

{% highlight text %}
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
remote: This repository moved. Please use the new location:
remote:   (Repository URL)
remote: error: GH007: Your push would publish a private email address.
remote: You can make your email public or disable this protection by visiting:
remote: http://github.com/settings/emails
To (Repository URL)
 ! [remote rejected] main -> main (push declined due to email privacy restrictions)
error: failed to push some refs to '(Repository URL)'
{% endhighlight %}

<br/>

# 해결

[이메일 설정](http://github.com/settings/emails) 페이지로 가서 하단의 **Block command line pushes that expose my email** 체크를 풀어주어야 한다.
해당 페이지는 Your Settings -> Access -> Emails에서 확인할 수 있다.

- English ver

![github](/assets/img/post_img/war_jsp/git.png)

- 한국어 ver

![github](/assets/img/post_img/war_jsp/gitko.png)

