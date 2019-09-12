---
layout: post
title: "Jekyll Liquid 태그"
date: 2019-09-10
categories: jekyll
---

post 글을 확인하려고 `bundle exec jekyll serve` 명령어를 실행하던 중 에러가 발생했다.
```bash
Liquid Exception: Could not find document 'foo.md' in tag 'link'. Make sure the document exists and the path is correct. in D:/workspace/blog/jdae02.github.io/_posts/2019-09-10-error-bundler.md
                 ------------------------------------------------
   Jekyll 4.0.0   Please append `--trace` to the `serve` command
                  for any additional information or backtrace.
                 ------------------------------------------------
```
포스트 파일에 Liquid 태그가 {% raw %}`{% %}`{% endraw %} 그대로 노출되었기 때문에 발생하였다.
raw 태그 안에 Liquid 태그를 입력해야 정상적으로 표시할 수 있다.

{% raw %}`{% raw %} Liquid 태그 {% endraw % }`{% endraw %}

더 간단한 방법으로 4.0 버전부터는 render_with_liquid: false 옵션 추가만으로 Liquid 태그를 자유롭게 입력할 수 있다.
다만 이 경우에는 당연하겠지만 syntax highlighting 기능을 사용할 수 없다.

{% raw %}`{% highlight ruby %}`{% endraw %}


>Jekyll processes all Liquid filters in code blocks
>
>If you are using a language that contains curly braces, you will likely need to place {% raw %}{% raw %} and {% endraw % }{% endraw %} tags around your code. Since 4.0 you can add render_with_liquid: false in your front matter to disable Liquid entirely for a particular document.

[https://jekyllrb.com/docs/liquid/tags/](https://jekyllrb.com/docs/liquid/tags/)

github에 올리는데 계속 에러가 발생하여 찾아본 결과
render_with_liquid: false 옵션은 이 상태로는 사용할 수가 없다.  
**github의 jekyll 버전이 4.0보다 낮기 때문이다.**

이게 안되더라도 더 쉬운 방법이 어딘가에 있을 수 있겠지만, 에러가 꼬리에 꼬리를 물고 계속 나타나니...
github 블로그 참 어렵네.
