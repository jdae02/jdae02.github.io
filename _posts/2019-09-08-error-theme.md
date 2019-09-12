---
layout: post
title:  "Failed at the node-sass@3.13.1 postinstall script"
date:   2019-09-08
categories: error
---

Jekyll [LONG HAUL][long-haul] 테마를 설치하던 중 에러가 발생했다.
Setup 과정을 보면 `npm install` 후에 `bundle exec gulp`를 실행하라고 나와있다.
그런데 여기서 에러가 발생했다.

{% highlight bash %}
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! node-sass@3.13.1 postinstall: `node scripts/build.js`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the node-sass@3.13.1 postinstall script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
{% endhighlight %}

`package.json`을 보면 `node-sass` 모듈이 `devDependencies`에 포함이 되어있어 설치가 될텐데 왜 에러가 발생했는지 알 수가 없다.
구글링을 통해 [깃허브][github-link] 에서 해답을 찾았다.
스크롤을 내리면 좋아요가 잔뜩 달려있는 댓글이 보이는데,
좀 더 내려보니 좋아요 많고 순서가 적혀있는 댓글이 보인다.
1. node_modules를 지우고
2. package.json에서 gulp-sass를 지우고
3. package.json에서 node-sass를 지우고
4. npm install gulp-sass --save-dev 다시 설치해서 package.json에 등록

`node_modules`를 지웠으므로 다시 `npm install`을 해주어야 한다.
`npm install gulp -g` 옵션으로 따로 설치했었는데, 이것 때문에 버전 차이로 인한 에러가 발생한 것으로 보인다.
 `bundle exec gulp` 다시 실행을 해보니 정상적으로 동작하는 것을 확인했다.

하지만 테마를 적용하진 않았다.

[long-haul]: https://brianmaierjr.com/long-haul/
[github-link]: https://github.com/codecombat/codecombat/issues/4430
