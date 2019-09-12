---
layout: post
title: "(Bundler::GemNotFound)"
date: 2019-09-10
categories: jekyll
---

한군데서 작업하는 것이 아니라 각각 버전이 다를 수 있다.
jekyll 설치했던 날짜들이 달라서 버전이 맞지 않아 그런지 문제가 발생했다.

```bash
$ bundle exec jekyll serve
C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/spec_set.rb:87:in `block in materialize': Could not find jekyll-feed-0.12.1 in any of the sources (Bundler::GemNotFound)
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/spec_set.rb:81:in `map!'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/spec_set.rb:81:in `materialize'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/definition.rb:170:in `specs'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/definition.rb:237:in `specs_for'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/definition.rb:226:in `requested_specs'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/runtime.rb:108:in `block in definition_method'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/runtime.rb:20:in `setup'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler.rb:107:in `setup'
        from C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/lib/bundler/setup.rb:20:in `<top (required)>'
        from C:/Ruby26-x64/lib/ruby/2.6.0/rubygems/core_ext/kernel_require.rb:54:in `require'
        from C:/Ruby26-x64/lib/ruby/2.6.0/rubygems/core_ext/kernel_require.rb:54:in `require'
```

루비를 지우고 새로 설치하는 방법도 있겠지만 업데이트를 통해 해결하려고 한다.
약간의 시행착오 끝에 해결의 실마리를 찾았다.
[스택오버플로우 답변][stackoverflow]을 보면 bundler의 경로에 문제가 있으니 다음 명령어로 수정하라는 것이다.
`bundle install --path vendor/cache`
기존에 global로 설치된 bundler가 문제였던건지 모르겠다.

{% raw %}
```bash
...
Bundle complete! 6 Gemfile dependencies, 35 gems now installed.
Bundled gems are installed into `./vendor/cache`
Post-install message from i18n:

HEADS UP! i18n 1.1 changed fallbacks to exclude default locale.
But that may break your application.

Please check your Rails app for 'config.i18n.fallbacks = true'.
If you're using I18n (>= 1.1.0) and Rails (< 5.2.2), this should be
'config.i18n.fallbacks = [I18n.default_locale]'.
If not, fallbacks will be broken in your app by I18n 1.1.x.

For more info see:
https://github.com/svenfuchs/i18n/releases/tag/v1.1.0

Post-install message from jekyll:
-------------------------------------------------------------------------------------
Jekyll 4.0 comes with some major changes, notably:
  * Our `link` tag now comes with the `relative_url` filter incorporated into it.
    You should no longer prepend `{{ site.baseurl }}` to `{% link foo.md %}`
    For further details: https://github.com/jekyll/jekyll/pull/6727

  * Our `post_url` tag now comes with the `relative_url` filter incorporated into it.
    You shouldn't prepend `{{ site.baseurl }}` to `{% post_url 2019-03-27-hello %}`
    For further details: https://github.com/jekyll/jekyll/pull/7589

  * Support for deprecated configuration options has been removed. We will no longer
    output a warning and gracefully assign their values to the newer counterparts
    internally.
-------------------------------------------------------------------------------------
```
{% endraw %}

[stackoverflow]: https://stackoverflow.com/questions/23801899/bundlergemnotfound-could-not-find-rake-10-3-2-in-any-of-the-sources
