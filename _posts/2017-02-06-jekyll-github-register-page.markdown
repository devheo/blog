---
layout: post
title:  "jekyll로 github 시작하기"
date:   2017-02-06 15:38:27 +0900
categories: jekyll github
---
블로그를 다시 시작해볼까? 라는 마음으로 이전에 사용하던 티스토리 계정을 열어보았습니다만, 다시 시작하려 하니 플러그인 설치들과 같은 일로 시간을 낭비하는 것보다 심플함과 개방성, 기록을 하기 위한 블로그를 만들려다가 생각했던 것이 깃이었습니다만, HTML 페이지를 일일이 만들려고 시간낭비 하는 것에 대한 고민을 했습니다. 그러다보니 마크다운을 알게 되었고, Jekyll을 알게 되었습니다.

# Jekyll 이란 무엇인가?
Jekyll이란 공식사이트[jekyll-docs-home]에서 나와있는 설명을 하면 간단하고 단순한 사이트 생성기라고 합니다. 
Markdown 같은 형태의 포멧을 HTML 포멧 형태로 변환해 주는 일을 하며, 서버에 배포까지 할 수 있으며, 파일 수정시 자동으로 재배포 할 수 있도록 실시간 반영이 됩니다.
이렇게 사용자는 Markdown 형태의 파일을 작성하면 HTML로 변환하여 주기 때문에 별 다른 설정이 필요없이 사용할 수 있습니다.
제가 사용하면서 가장 좋았던 점은 로컬에서 테스트하여 실시간으로 볼 수 있다는 점이 제일 좋은 것 같습니다.

# Github와 Jekyll을 같이 사용하는가?
Github에서 Jekyll을 공식적으로 지원하며, 제일 좋은 점은 소스 관리 측면인 것 같습니다. 게다가 Jekyll과 Github에서는 무료로 사용할 수 있다고 나와 있으니까요. 이렇게 되면 원격지나 Jekyll을 설치하지 않아도 Markdown 파일 작성만으로도 어디에서나 업로드가 가능하다는 장점도 있겠네요. 

# Jekyll 설치
제가 사용하는 OS는 MAC이다 보니 MAC을 중심으로 설명토록 하겠습니다.
MAC에서 설치하기 위해서는 Xcode가 설치되어 있어야 하며, 
{% highlight shell %}
$ sudo gem install jekyll
{% endhighlight %}

설치가 완료가 되었다면, 아래의 명령어를 사용하여 블로그를 생성합니다. 
저의 Github아이디가 devheo 이니, 'devheo.github.io' 와 같이 생성하시면 되겠습니다. 
왜 이런 형태로 만드냐하면은 로컬과 원격지의 폴더구조를 동일시하게 되면 여러모로 편리해서 그렇게 많이들 사용합니다.
{% highlight shell %}
$ jekyll new [your-awesome-site]
{% endhighlight %}
위와 같이 실행을 하고 나면 아래와 같이 'your-awesome-site'에서 입력한 폴더가 생성됩니다. 저는 'devheo.github.com'으로 생성하였기에 아래와 같이 생성 되었습니다. 
이제 로컬에서 서버를 실행해보도록 하겠습니다. 아래와 같이 실행해주세요.
{% highlight shell %}
$ jekyll serve
#=> 또는 아래와 같이 입력해도 상관 없습니다. 동일 명령어니깐요. 공식페이지에는 아래와 같이 나와있네요.
$ bundle exec jekyll serve
{% endhighlight %}
서버가 문제없이 실행된다면 브라우져상에서 'localhost:4000'을 실행을 하시면, 
이상이 없다면 아래와 같이 실행이 될 것입니다. 
![Alt text](https://c1.staticflickr.com/1/442/32719884816_c42db1b448_b.jpg, "web page")

이제 로컬저장소에서 테스트 할 수 있는 환경은 다 구축되었으며, 실제로 github와 연동할 수 있도록 하기 위해서는 [Github 가입과 Repository만들기][git-blog-register]를 참조하여 로컬에 만든 폴더위치에서 실행하시면 됩니다.

<br>
# Trouble Shooting
만약 설치시 위와 같은 에러가 발생한다면 아래와 같이 gem update 또는 아래와 같이 설치 및 해보시기 바랍니다. 
저는 아래와 같은 에러를 겪었네요.

<img src="https://c1.staticflickr.com/1/325/31945486473_0ad7feffb4_k.jpg" width="630" height="45"/>

위와 같은 에러들 발생시 아래와 같이 터미널에서 시도해 보시기 바랍니다. 
{% highlight shell %}
$ sudo gem update --system
$ sudo gem install bundler 
#=> bundler가 설치가 되어있지 않을 수도 있구요.
$ sudo bundle install 
#=> dependencies 설치 및 업데이트가 필요한 경우도 있구요.
{% endhighlight %}

혹시 Permission 문제가 발생한다면터미널에서 ll을 실행해보자.
ex) ll를 실행했을 때 user가 아니라 root로 폴더가 설정되어 있을 경우가 있습니다.

![Alt text](https://c1.staticflickr.com/1/566/31946506003_1c086a3d46_z.jpg, "Permission Problem")

이럴 때에는 디렉토리 권한을 아래와 같이 변경해주세요.
{% highlight shell %}
$ sudo chmod username:group directory 
{% endhighlight %}
<br>
# 참고 자료
1. Link: [jekyll 공식 사이트][jekyll-docs-home]
2. Link: [jekyll 한글 번역 사이트][jekyll-docs-kr]
3. Link: [놀부의 지킬로 깃허브에 무료 블로그 만들기]

[git-blog-register]: https://devheo.github.io/blog/test/pages/2017/02/03/git-register-page.html
[jekyll-docs-home]: https://jekyllrb.com/docs/home/
[jekyll-docs-kr]: https://jekyllrb-ko.github.io
[jekyll-docs-usage]: https://jekyllrb-ko.github.io/docs/usage/
[jekyll-docs-template]: https://jekyllrb-ko.github.io/docs/templates/
[jekyll-docs-documentation]: http://import.jekyllrb.com/docs/home/
[nolboo-jekyll-post]: https://nolboo.kim/blog/2013/10/15/free-blog-with-github-jekyll/

