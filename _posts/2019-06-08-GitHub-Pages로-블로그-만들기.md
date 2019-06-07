---
categories:
- posts
tags:
- blog
- jekkly
---

## 깃허브에서 리포지토리 생성하기
깃허브에서 리포지토리를 생성하는 방법은 매우 간단하다.  
리포지토리를 생성할 때 리포지토리명과 사용자명이 일치하지 않으면 올바르게 동작하지 않음으로 이 점만 주의하면 된다.  
아래 이미지처럼 리포지토리명에 "username.github.io"를 입력하고 생성버튼을 클릭하는 것으로 깃허브에서 정적파일을 호스팅할 모든 준비는 끝이난다.

![](/assets/images/2019/2019-001.png)

이후 정적파일 호스팅이 잘 되는지 테스트해 볼 목적으로 index.html을 작성하여 리포지토리에 푸쉬한다.<br><br>
index.html:  
{% highlight html %}
<!DOCTYPE html>
<html>
<body>
<h1>Hello World!!</h1>
</body>
</html>
{% endhighlight %}

이제 브라우저에서 "https://username.github.io/" 로 접근하면 Hello World 보여진다.  
이로써 Github Pages에서 정적파일을 호스팅해주는 모든 준비를 맞췄다.

## 지킬(Jekyll)
지킬은 매우 간단하고 유연한 정적 웹사이트 생성기이다. 즉, 사용자는 HTML, Markdown 등의 마크업 언어로 컨텐츠를 작성하면 지킬은 이를 빌드하여 정적 파일을 생성한다. 또한, 깃허브에서 지키를 자체적으로 지원하기에 깃허브 리포지토리에 문서만 푸쉬하면 된다. 이런 간단한 절차로 인해 사용자는 컨텐츠에만 집중 할 수 있고 이건 지킬을 사용하는 매우 큰 장점이다.


### 지킬 설치하기
지킬은 루비(Ruby)기반이다. 맥에는 루비가 내장 설치되어 있어서 루비를 설치할 필요 없이 아래 한줄이면 설치가 끝난다.   
```
gem install jekyll bundler
```

### 지킬 테마
테마는 Minimal Mistakes를 적용한다. 이 테마는 워낙 문서가 잘 작성되어 있어서 링크로 대체한다.  
[minimal-mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/){:target="_blank"}


## 고유 도메인 설정하기
생성한 블로그는 브라우저에서 https://username.github.io 로 접근해야 한다. 이 접근 URL을 내가 가지고 있는 고유 도메인으로 변경하려 한다.<br><br>
우선 웹호스팅 업체에서 도메인을 구매한다. 나는 기존에 이용하고 있던 후이즈에서 도메인을 구매하였다.<br><br>
도메인을 구매하였다면 다음으로 리포지토리의 Settings.GitHub Pages 섹션에서 구매한 도메인을 등록한다.  
![](/assets/images/2019/2019-002.png)<br><br>

마지막으로 아래 링크에 나오는 IP주소를 구매한 도메인의 네임서버에 A레코드로 추가하면 끝이다.
![](/assets/images/2019/2019-003.png)  

깃허브와 지킬로 블로그 생성과 도메인 연결은 완료하였다. 테마를 커스텀하여 블로그를 더욱 예쁘게 꾸며야 하는데 그건 포스트를 어느정도 등록한 시점에 진행하기로 한다.