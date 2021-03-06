---
layout: post
title: "Git 저장소 생성부터 저장까지"
date: 2017-02-08 14:46:00 +0900
categories: Git
---

현재 폴더에 새로운 git 저장소를 만듭니다. 현재 폴더를 git 저장소로 변환한다고 하는것이 더 맞는 표현일 수도 있겠네요. 생성이 완료되면 .git 폴더가 폴더내에 생성된 것을 확인하실 수 있습니다. `git init` 명령어가 바로 저장소를 만드는 명령어 입니다. 

{% highlight shell %}
$ git init
{% endhighlight %}

로컬 저장소를 만들었으면, 파일을 생성하도록 하겠습니다.
{% highlight shell %}
$ echo "hello git world" > README.md 
#=> README.md 파일에 "hello git world" 라고 내용을 작성하고 파일을 생성하였습니다.
$ touch README.md
#=> 이렇게 파일만 생성해도 됩니다.
{% endhighlight %}

git 저장소 내에 파일이 생성하였으면 git 저장소의 상태를 한 번 알아보겠습니다.
`git status` 는 형재 저장소의 상태를 알아볼 때 사용하는 명령어 입니다.
{% highlight shell %}
$ git status
#=> 현재 저장소의 상태를 확인하는 명령어 입니다.
{% endhighlight %}

위에서 README.md 파일을 추가하였지만, Untracked files 상태로 되어있을 있을 것입니다.
{% highlight shell %}
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

      README.md

nothing added to commit but untracked files present (use "git add" to track)
#=> 간략하게 상태들을 확인하고 싶다면 -s 옵션을 추가하면 된다. short의 줄임 옵션인 듯
$ git status -s
M blog
?? README.md
#=> Untracked file 일 경우 '??' 마크로 표시하며, 'M'은 modified, 'A'는 tracked.
{% endhighlight %}

git에서는 untracked file이라는 것은 아직 커밋하지 않은 파일이라고 않은 상태, 즉 git의 타겟이 되지 않는 상태이기 때문에, commit을 하더라도 절대 untracked 상태에 있는 파일들은 제외된다. 

파일을 tracked 상태로 바꾸기 위해서는 `git add` 라는 명령어를 사용합니다. 아래와 같이 여러 옵션을 주어 사용할 수 있으며, 명령이 실행되면 대상파일이 tracked 상태로 변경이 된다.

{% highlight shell %}
$ git add README.md 
#=> README.md 파일을 저장소에 track 할 수 있도록 추가한다.
$ git add .
#=> 현재 폴더 내에 수정되거나 추가/삭제된 모든 파일들을 track 하도록 한다.
$ git add --all
#=> "git add ."을 포함하고, sub directory까지 track 하도록 하는 옵션이다.
{% endhighlight %}

이제 수정하거나 추가한 파일들을 저장소에 올리려면 `git commit` 명령어를 사용한다. 이 명령어는 tracked 상태에 있는 모든 파일들을 커밋한다. `-m` 은 message의 줄임말로 무엇때문에 커밋하는지에 대한 이력을 꼭 남겨야 한다. 
{% highlight shell %}
$ git commit -m "add file README.md"
{% endhighlight %}

파일을 제거하려면 `git rm` 명령어를 사용한다. 제거될 파일은 tracked 상태여야 한다. 이 명령어를 사용하면 실제 현재 워킹 디렉토리에도 파일이 삭제된다.

{% highlight shell %}
$ git rm README.md 
{% endhighlight %}

파일을 변경하려면 `git mv` 명령어를 사용한다. 제거와 변경 명령어를 보면 알겠지만 유닉스의 `mv/rm` 명령어와 똑같다. 
{% highlight shell %}
$ git mv README.md README
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

      renamed:    README.md -> README
{% endhighlight %}


