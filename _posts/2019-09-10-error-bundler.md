---
layout: post
title: "(Bundler::GemNotFound)"
date: 2019-09-10
categories: error jekyll
render_with_liquid: false
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

```bash
Fetching gem metadata from https://rubygems.org/...........
Fetching public_suffix 4.0.1
Installing public_suffix 4.0.1
Fetching addressable 2.7.0
Installing addressable 2.7.0
Using bundler 2.0.2
Fetching colorator 1.1.0
Installing colorator 1.1.0
Fetching concurrent-ruby 1.1.5
Installing concurrent-ruby 1.1.5
Fetching eventmachine 1.2.7 (x64-mingw32)
Installing eventmachine 1.2.7 (x64-mingw32)
Fetching http_parser.rb 0.6.0
Installing http_parser.rb 0.6.0 with native extensions
Fetching em-websocket 0.5.1
Installing em-websocket 0.5.1
Fetching ffi 1.11.1 (x64-mingw32)
Installing ffi 1.11.1 (x64-mingw32)
Fetching forwardable-extended 2.6.0
Installing forwardable-extended 2.6.0
Fetching i18n 1.6.0
Installing i18n 1.6.0
Fetching sassc 2.2.0 (x64-mingw32)
Installing sassc 2.2.0 (x64-mingw32)
Fetching jekyll-sass-converter 2.0.0
Installing jekyll-sass-converter 2.0.0
Fetching rb-fsevent 0.10.3
Installing rb-fsevent 0.10.3
Fetching rb-inotify 0.10.0
Installing rb-inotify 0.10.0
Fetching ruby_dep 1.5.0
Installing ruby_dep 1.5.0
Fetching listen 3.1.5
Installing listen 3.1.5
Fetching jekyll-watch 2.2.1
Installing jekyll-watch 2.2.1
Fetching kramdown 2.1.0
Installing kramdown 2.1.0
Fetching kramdown-parser-gfm 1.1.0
Installing kramdown-parser-gfm 1.1.0
Fetching liquid 4.0.3
Installing liquid 4.0.3
Fetching mercenary 0.3.6
Installing mercenary 0.3.6
Fetching pathutil 0.16.2
Installing pathutil 0.16.2
Fetching rouge 3.10.0
Installing rouge 3.10.0
Fetching safe_yaml 1.0.5
Installing safe_yaml 1.0.5
Fetching unicode-display_width 1.6.0
Installing unicode-display_width 1.6.0
Fetching terminal-table 1.8.0
Installing terminal-table 1.8.0
Fetching jekyll 4.0.0
Installing jekyll 4.0.0
Fetching jekyll-feed 0.12.1
Installing jekyll-feed 0.12.1
Fetching jekyll-seo-tag 2.6.1
Installing jekyll-seo-tag 2.6.1
Fetching minima 2.5.1
Installing minima 2.5.1
Fetching thread_safe 0.3.6
Installing thread_safe 0.3.6
Fetching tzinfo 1.2.5
Installing tzinfo 1.2.5
Fetching tzinfo-data 1.2019.2
Installing tzinfo-data 1.2019.2
Fetching wdm 0.1.1
Installing wdm 0.1.1 with native extensions
Updating files in vendor/cache
  * public_suffix-4.0.1.gem
  * addressable-2.7.0.gem
  * colorator-1.1.0.gem
  * concurrent-ruby-1.1.5.gem
  * eventmachine-1.2.7-x64-mingw32.gem
  * http_parser.rb-0.6.0.gem
  * em-websocket-0.5.1.gem
  * ffi-1.11.1-x64-mingw32.gem
  * forwardable-extended-2.6.0.gem
  * i18n-1.6.0.gem
  * sassc-2.2.0-x64-mingw32.gem
  * jekyll-sass-converter-2.0.0.gem
  * rb-fsevent-0.10.3.gem
  * rb-inotify-0.10.0.gem
  * ruby_dep-1.5.0.gem
  * listen-3.1.5.gem
  * jekyll-watch-2.2.1.gem
  * kramdown-2.1.0.gem
  * kramdown-parser-gfm-1.1.0.gem
  * liquid-4.0.3.gem
  * mercenary-0.3.6.gem
  * pathutil-0.16.2.gem
  * rouge-3.10.0.gem
  * safe_yaml-1.0.5.gem
  * unicode-display_width-1.6.0.gem
  * terminal-table-1.8.0.gem
  * jekyll-4.0.0.gem
  * jekyll-feed-0.12.1.gem
  * jekyll-seo-tag-2.6.1.gem
  * minima-2.5.1.gem
  * thread_safe-0.3.6.gem
  * tzinfo-1.2.5.gem
  * tzinfo-data-1.2019.2.gem
  * wdm-0.1.1.gem
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

[stackoverflow]: https://stackoverflow.com/questions/23801899/bundlergemnotfound-could-not-find-rake-10-3-2-in-any-of-the-sources
