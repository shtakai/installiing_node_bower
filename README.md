# node.jsとbowerのインストール(homebrewから)

[![GuardRails badge](https://badges.production.guardrails.io/shtakai/installiing_node_bower.svg)](https://www.guardrails.io)

ndenv等でnode.jsのバージョンわけをするときは別途。

## 事前にインストールしておく
- OSX
- ターミナル、itermが起動できる https://techacademy.jp/magazine/5155
- xcodeとコマンドラインツールがインストールされている
- xcode起動、終了、コマンドラインツールの起動確認も行う http://qiita.com/s_0_a_r_/items/4233cf9df5af654a6109#xcode-command-line-tools%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB
```terminal
$git --version
$ git --version
git version 2.11.0 ←バージョンが表示されればOK
```

## homebrewのインストール
- ここをを見て http://brew.sh/index_ja.html

- ターミナルからインストール
```terminal
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## node.jsのインストール
- ターミナルからインストール
```terminal
$ brew install nodejs
```
```terminal
$ brew --version
Homebrew 1.1.6
Homebrew/homebrew-core (git revision 9c73d; last commit 2017-01-09) ←バージョンが表示されればOK
```
- ターミナルからnode.jsが動くか確認
```terminal
$ node --version
v6.9.2 ←バージョンが表示されればOK
$ npm --version
3.10.9 ←バージョンが表示されればOK
```

## bowerのインストール
- ターミナルからインストール
```terminal
$ npm install -g bower
$ bower --version
1.8.0 ←バージョンが表示されればOK
```

## ここまででできること
- javascriptエンジンの起動(node.js)
```terminal
$ node
> console.log('test')
test ←console.logの内容が表示
undefined
> .exit
```

- bowerによるjsパッケージのインストール
```terminal
(例:新しくbowerのプロジェクトファイルを作る場合)
$ cd ~/tmp
$ mkdir bower_test
$ cd bower_test/
$ bower init
? name bower_test
? description
? main file
? keywords
? authors Alyson T <shtakai@gmail.com>
? license MIT
? homepage
? set currently installed components as dependencies? Yes
? add commonly ignored files to ignore list? Yes
? would you like to mark this package as private which prevents it from being accidentally published to the registry? No

{
  name: 'bower_test',
  authors: [
    'Username <email@email.com'>
  ],
  description: '',
  main: '',
  license: 'MIT',
  homepage: '',
  ignore: [
    '**/.*',
    'node_modules',
    'bower_components',
    'test',
    'tests'
  ]
}

? Looks good? Yes

$ bower install -save jquery
bower jquery#*                  cached https://github.com/jquery/jquery-dist.git#3.1.1
bower jquery#*                validate 3.1.1 against https://github.com/jquery/jquery-dist.git#*
bower jquery#^3.1.1            install jquery#3.1.1

jquery#3.1.1 bower_components/jquery
```

```terminal
(例:リモートにプロジェクトがあり、そこからcloneしてインストールする場合)
$ cd ~/tmp
$ git clone https://github.com/nimhawk/bower_playground.git
Cloning into 'bower_playground'...
remote: Counting objects: 12, done.
remote: Total 12 (delta 0), reused 0 (delta 0), pack-reused 12
Unpacking objects: 100% (12/12), done.
$ cd bower_playground/
$ bower install
bower jquery#~2.0.3         not-cached https://github.com/jquery/jquery-dist.git#~2.0.3
bower jquery#~2.0.3            resolve https://github.com/jquery/jquery-dist.git#~2.0.3
bower hogan#~3.0.0          not-cached https://github.com/twitter/hogan.js.git#~3.0.0
bower hogan#~3.0.0             resolve https://github.com/twitter/hogan.js.git#~3.0.0
bower underscore#~1.5.2     not-cached https://github.com/jashkenas/underscore.git#~1.5.2
bower underscore#~1.5.2        resolve https://github.com/jashkenas/underscore.git#~1.5.2
bower backbone#~1.0.0       not-cached https://github.com/jashkenas/backbone.git#~1.0.0
bower backbone#~1.0.0          resolve https://github.com/jashkenas/backbone.git#~1.0.0
bower jquery#~2.0.3           download https://github.com/jquery/jquery-dist/archive/2.0.3.tar.gz
bower hogan#~3.0.0            download https://github.com/twitter/hogan.js/archive/v3.0.2.tar.gz
bower underscore#~1.5.2       download https://github.com/jashkenas/underscore/archive/1.5.2.tar.gz
bower backbone#~1.0.0         download https://github.com/jashkenas/backbone/archive/1.0.0.tar.gz
bower jquery#~2.0.3            extract archive.tar.gz
bower hogan#~3.0.0             extract archive.tar.gz
bower hogan#~3.0.0          deprecated Package hogan is using the deprecated component.json
bower jquery#~2.0.3           resolved https://github.com/jquery/jquery-dist.git#2.0.3
bower hogan#~3.0.0            resolved https://github.com/twitter/hogan.js.git#3.0.2
bower underscore#~1.5.2        extract archive.tar.gz
bower underscore#~1.5.2       resolved https://github.com/jashkenas/underscore.git#1.5.2
bower backbone#~1.0.0          extract archive.tar.gz
bower backbone#~1.0.0         resolved https://github.com/jashkenas/backbone.git#1.0.0
bower jquery#~2.0.3            install jquery#2.0.3
bower hogan#~3.0.0             install hogan#3.0.2
bower underscore#~1.5.2        install underscore#1.5.2
bower backbone#~1.0.0          install backbone#1.0.0

jquery#2.0.3 bower_components/jquery

hogan#3.0.2 bower_components/hogan

underscore#1.5.2 bower_components/underscore

backbone#1.0.0 bower_components/backbone

$ tree
.
├── LICENSE
├── README.md
├── bower.json
└── bower_components
    ├── backbone
    │   ├── CNAME
    │   ├── CONTRIBUTING.md
    │   ├── LICENSE
    │   ├── README.md
    │   ├── Rakefile
    │   ├── backbone-min.js
    │   ├── backbone-min.map
    │   ├── backbone.js
    │   ├── docs
    │   │   ├── backbone-localstorage.html
    │   │   ├── backbone.html
    │   │   ├── backbone.localstorage.html
    │   │   ├── docco.css
    │   │   ├── images
    │   │   │   ├── airbnb.png
    │   │   │   ├── arrows.png
    │   │   │   ├── artsy.png
    │   │   │   ├── backbone-mobile.png
    │   │   │   ├── backbone.png
    │   │   │   ├── background.png
    │   │   │   ├── baroque.jpg
    │   │   │   ├── basecamp-calendar.jpg
    │   │   │   ├── battlefield.png
    │   │   │   ├── bitbucket.png
    │   │   │   ├── blossom.png
    │   │   │   ├── cloudapp.png
    │   │   │   ├── code-school.png
    │   │   │   ├── dc-workspace.png
    │   │   │   ├── diaspora.png
    │   │   │   ├── disqus.png
    │   │   │   ├── do.png
    │   │   │   ├── easel.png
    │   │   │   ├── favicon.ico
    │   │   │   ├── flow.png
    │   │   │   ├── foursquare.png
    │   │   │   ├── gilt.jpg
    │   │   │   ├── groupon.png
    │   │   │   ├── hulu.png
    │   │   │   ├── inkling.png
    │   │   │   ├── irccloud.png
    │   │   │   ├── jolicloud.jpg
    │   │   │   ├── khan-academy.png
    │   │   │   ├── linkedin-mobile.png
    │   │   │   ├── menagerievet.png
    │   │   │   ├── newsblur.jpg
    │   │   │   ├── pandora.png
    │   │   │   ├── pitchfork.png
    │   │   │   ├── prose.png
    │   │   │   ├── quartz.jpg
    │   │   │   ├── rdio.png
    │   │   │   ├── salon.png
    │   │   │   ├── seatgeek.png
    │   │   │   ├── slavery-footprint.png
    │   │   │   ├── soundcloud.png
    │   │   │   ├── spin.png
    │   │   │   ├── stripe.png
    │   │   │   ├── syllabus.jpg
    │   │   │   ├── tilemill.png
    │   │   │   ├── todos.png
    │   │   │   ├── trello.png
    │   │   │   ├── tzigla.png
    │   │   │   ├── usa-today.png
    │   │   │   ├── walmart-mobile.png
    │   │   │   └── wpcom-notifications.png
    │   │   ├── js
    │   │   │   └── jquery.lazyload.js
    │   │   ├── jsl.conf
    │   │   ├── public
    │   │   │   ├── fonts
    │   │   │   │   ├── aller-bold.eot
    │   │   │   │   ├── aller-bold.ttf
    │   │   │   │   ├── aller-bold.woff
    │   │   │   │   ├── aller-light.eot
    │   │   │   │   ├── aller-light.ttf
    │   │   │   │   ├── aller-light.woff
    │   │   │   │   ├── fleurons.eot
    │   │   │   │   ├── fleurons.ttf
    │   │   │   │   ├── fleurons.woff
    │   │   │   │   ├── novecento-bold.eot
    │   │   │   │   ├── novecento-bold.ttf
    │   │   │   │   └── novecento-bold.woff
    │   │   │   ├── images
    │   │   │   │   └── grey_@2X.png
    │   │   │   └── stylesheets
    │   │   │       └── normalize.css
    │   │   └── todos.html
    │   ├── examples
    │   │   ├── backbone.localStorage.js
    │   │   └── todos
    │   │       ├── destroy.png
    │   │       ├── index.html
    │   │       ├── todos.css
    │   │       └── todos.js
    │   ├── index.html
    │   ├── index.js
    │   ├── package.json
    │   └── test
    │       ├── collection.js
    │       ├── environment.js
    │       ├── events.js
    │       ├── index.html
    │       ├── model.coffee
    │       ├── model.js
    │       ├── noconflict.js
    │       ├── router.js
    │       ├── sync.js
    │       ├── vendor
    │       │   ├── jquery.js
    │       │   ├── json2.js
    │       │   ├── qunit.css
    │       │   ├── qunit.js
    │       │   ├── runner.js
    │       │   └── underscore.js
    │       └── view.js
    ├── hogan
    │   ├── LICENSE
    │   ├── Makefile
    │   ├── README.md
    │   ├── bin
    │   │   └── hulk
    │   ├── component.json
    │   ├── lib
    │   │   ├── compiler.js
    │   │   ├── hogan.js
    │   │   └── template.js
    │   ├── package.json
    │   ├── test
    │   │   ├── html
    │   │   │   └── list.html
    │   │   ├── hulk.js
    │   │   ├── index.html
    │   │   ├── index.js
    │   │   ├── jquery.js
    │   │   ├── json2.js
    │   │   ├── mustache.js
    │   │   ├── phantom-js-loader.js
    │   │   ├── qunit
    │   │   ├── qunit-logging
    │   │   ├── run.js
    │   │   ├── spec
    │   │   ├── spec.js
    │   │   ├── specWithGet.js
    │   │   └── templates
    │   │       └── list.mustache
    │   └── web
    │       ├── 1.0.0
    │       │   ├── hogan.js
    │       │   └── hogan.min.js
    │       ├── builds
    │       │   ├── 1.0.0
    │       │   │   ├── hogan.js
    │       │   │   └── hogan.min.js
    │       │   ├── 1.0.3
    │       │   │   ├── hogan.js
    │       │   │   └── hogan.min.js
    │       │   ├── 1.0.4
    │       │   │   ├── hogan-1.0.4.amd.js
    │       │   │   ├── hogan-1.0.4.common.js
    │       │   │   ├── hogan-1.0.4.js
    │       │   │   ├── hogan-1.0.4.min.amd.js
    │       │   │   ├── hogan-1.0.4.min.common.js
    │       │   │   ├── hogan-1.0.4.min.js
    │       │   │   ├── hogan-1.0.4.min.mustache.js
    │       │   │   ├── hogan-1.0.4.mustache.js
    │       │   │   ├── template-1.0.4.js
    │       │   │   └── template-1.0.4.min.js
    │       │   ├── 1.0.5
    │       │   │   ├── hogan-1.0.5.amd.js
    │       │   │   ├── hogan-1.0.5.common.js
    │       │   │   ├── hogan-1.0.5.js
    │       │   │   ├── hogan-1.0.5.min.amd.js
    │       │   │   ├── hogan-1.0.5.min.common.js
    │       │   │   ├── hogan-1.0.5.min.js
    │       │   │   ├── hogan-1.0.5.min.mustache.js
    │       │   │   ├── hogan-1.0.5.mustache.js
    │       │   │   ├── template-1.0.5.js
    │       │   │   └── template-1.0.5.min.js
    │       │   ├── 2.0.0
    │       │   │   ├── hogan-2.0.0.amd.js
    │       │   │   ├── hogan-2.0.0.common.js
    │       │   │   ├── hogan-2.0.0.js
    │       │   │   ├── hogan-2.0.0.min.amd.js
    │       │   │   ├── hogan-2.0.0.min.common.js
    │       │   │   ├── hogan-2.0.0.min.js
    │       │   │   ├── hogan-2.0.0.min.mustache.js
    │       │   │   ├── hogan-2.0.0.mustache.js
    │       │   │   ├── template-2.0.0.js
    │       │   │   └── template-2.0.0.min.js
    │       │   ├── 3.0.1
    │       │   │   ├── hogan-3.0.1.amd.js
    │       │   │   ├── hogan-3.0.1.common.js
    │       │   │   ├── hogan-3.0.1.js
    │       │   │   ├── hogan-3.0.1.min.amd.js
    │       │   │   ├── hogan-3.0.1.min.common.js
    │       │   │   ├── hogan-3.0.1.min.js
    │       │   │   ├── hogan-3.0.1.min.mustache.js
    │       │   │   ├── hogan-3.0.1.mustache.js
    │       │   │   ├── hogan.template-3.0.1.amd.js
    │       │   │   ├── hogan.template-3.0.1.common.js
    │       │   │   ├── hogan.template-3.0.1.js
    │       │   │   ├── hogan.template-3.0.1.min.amd.js
    │       │   │   ├── hogan.template-3.0.1.min.common.js
    │       │   │   ├── hogan.template-3.0.1.min.js
    │       │   │   ├── hogan.template-3.0.1.min.mustache.js
    │       │   │   └── hogan.template-3.0.1.mustache.js
    │       │   └── 3.0.2
    │       │       ├── hogan-3.0.2.amd.js
    │       │       ├── hogan-3.0.2.common.js
    │       │       ├── hogan-3.0.2.js
    │       │       ├── hogan-3.0.2.min.amd.js
    │       │       ├── hogan-3.0.2.min.common.js
    │       │       ├── hogan-3.0.2.min.js
    │       │       ├── hogan-3.0.2.min.mustache.js
    │       │       ├── hogan-3.0.2.mustache.js
    │       │       ├── template-3.0.2.js
    │       │       └── template-3.0.2.min.js
    │       ├── favicon.ico
    │       ├── images
    │       │   ├── logo.png
    │       │   ├── noise.png
    │       │   ├── small-hogan-icon.png
    │       │   └── stripes.png
    │       ├── index.html.mustache
    │       └── stylesheets
    │           ├── layout.css
    │           └── skeleton.css
    ├── jquery
    │   ├── AUTHORS.txt
    │   ├── CONTRIBUTING.md
    │   ├── Gruntfile.js
    │   ├── MIT-LICENSE.txt
    │   ├── README.md
    │   ├── bower.json
    │   ├── build
    │   │   ├── release-notes.js
    │   │   └── release.js
    │   ├── component.json
    │   ├── composer.json
    │   ├── jquery-migrate.js
    │   ├── jquery-migrate.min.js
    │   ├── jquery.js
    │   ├── jquery.min.js
    │   ├── jquery.min.map
    │   ├── package.json
    │   ├── speed
    │   │   ├── benchmark.js
    │   │   ├── benchmarker.css
    │   │   ├── benchmarker.js
    │   │   ├── closest.html
    │   │   ├── css.html
    │   │   ├── event.html
    │   │   ├── filter.html
    │   │   ├── find.html
    │   │   ├── index.html
    │   │   ├── jquery-basis.js
    │   │   └── slice.vs.concat.html
    │   ├── src
    │   │   ├── ajax
    │   │   │   ├── jsonp.js
    │   │   │   ├── script.js
    │   │   │   └── xhr.js
    │   │   ├── ajax.js
    │   │   ├── attributes.js
    │   │   ├── callbacks.js
    │   │   ├── core.js
    │   │   ├── css.js
    │   │   ├── data.js
    │   │   ├── deferred.js
    │   │   ├── deprecated.js
    │   │   ├── dimensions.js
    │   │   ├── effects.js
    │   │   ├── event-alias.js
    │   │   ├── event.js
    │   │   ├── exports.js
    │   │   ├── intro.js
    │   │   ├── manipulation.js
    │   │   ├── offset.js
    │   │   ├── outro.js
    │   │   ├── queue.js
    │   │   ├── selector-native.js
    │   │   ├── serialize.js
    │   │   ├── sizzle
    │   │   ├── sizzle-jquery.js
    │   │   ├── support.js
    │   │   ├── traversing.js
    │   │   └── wrap.js
    │   └── test
    │       ├── data
    │       │   ├── 1x1.jpg
    │       │   ├── ajax
    │       │   │   └── unreleasedXHR.html
    │       │   ├── atom+xml.php
    │       │   ├── badcall.js
    │       │   ├── badjson.js
    │       │   ├── cleanScript.html
    │       │   ├── core
    │       │   │   ├── cc_on.html
    │       │   │   ├── dont_return.php
    │       │   │   └── dynamic_ready.html
    │       │   ├── dashboard.xml
    │       │   ├── dimensions
    │       │   │   ├── documentLarge.html
    │       │   │   └── documentSmall.html
    │       │   ├── echoData.php
    │       │   ├── echoQuery.php
    │       │   ├── errorWithJSON.php
    │       │   ├── errorWithText.php
    │       │   ├── etag.php
    │       │   ├── evalScript.php
    │       │   ├── event
    │       │   │   ├── focusElem.html
    │       │   │   ├── longLoadScript.php
    │       │   │   ├── onbeforeunload.html
    │       │   │   ├── promiseReady.html
    │       │   │   └── syncReady.html
    │       │   ├── headers.php
    │       │   ├── if_modified_since.php
    │       │   ├── iframe.html
    │       │   ├── jquery-1.9.1.ajax_xhr.min.js
    │       │   ├── json.php
    │       │   ├── json_obj.js
    │       │   ├── jsonp.php
    │       │   ├── manipulation
    │       │   │   └── iframe-denied.html
    │       │   ├── name.html
    │       │   ├── name.php
    │       │   ├── nocontent.php
    │       │   ├── offset
    │       │   │   ├── absolute.html
    │       │   │   ├── body.html
    │       │   │   ├── fixed.html
    │       │   │   ├── relative.html
    │       │   │   ├── scroll.html
    │       │   │   ├── static.html
    │       │   │   └── table.html
    │       │   ├── params_html.php
    │       │   ├── readywaitasset.js
    │       │   ├── readywaitloader.js
    │       │   ├── script.php
    │       │   ├── selector
    │       │   │   ├── html5_selector.html
    │       │   │   └── sizzle_cache.html
    │       │   ├── statusText.php
    │       │   ├── support
    │       │   │   ├── bodyBackground.html
    │       │   │   ├── boxSizing.html
    │       │   │   ├── csp.js
    │       │   │   ├── csp.php
    │       │   │   ├── shrinkWrapBlocks.html
    │       │   │   └── testElementCrash.html
    │       │   ├── test.html
    │       │   ├── test.js
    │       │   ├── test.php
    │       │   ├── test2.html
    │       │   ├── test3.html
    │       │   ├── testinit.js
    │       │   ├── testrunner.js
    │       │   ├── testsuite.css
    │       │   ├── text.php
    │       │   ├── ua.txt
    │       │   ├── with_fries.xml
    │       │   └── with_fries_over_jsonp.php
    │       ├── delegatetest.html
    │       ├── hovertest.html
    │       ├── index.html
    │       ├── jquery.js
    │       ├── localfile.html
    │       ├── networkerror.html
    │       ├── qunit
    │       ├── readywait.html
    │       ├── unit
    │       │   ├── ajax.js
    │       │   ├── attributes.js
    │       │   ├── callbacks.js
    │       │   ├── core.js
    │       │   ├── css.js
    │       │   ├── data.js
    │       │   ├── deferred.js
    │       │   ├── deprecated.js
    │       │   ├── dimensions.js
    │       │   ├── effects.js
    │       │   ├── event.js
    │       │   ├── exports.js
    │       │   ├── manipulation.js
    │       │   ├── offset.js
    │       │   ├── queue.js
    │       │   ├── selector.js
    │       │   ├── serialize.js
    │       │   ├── support.js
    │       │   ├── traversing.js
    │       │   └── wrap.js
    │       └── xhtml.php
    └── underscore
        ├── CNAME
        ├── CONTRIBUTING.md
        ├── LICENSE
        ├── README.md
        ├── Rakefile
        ├── docs
        │   ├── docco.css
        │   ├── favicon.ico
        │   ├── images
        │   │   ├── background.png
        │   │   └── underscore.png
        │   ├── public
        │   │   ├── fonts
        │   │   │   ├── aller-bold.eot
        │   │   │   ├── aller-bold.ttf
        │   │   │   ├── aller-bold.woff
        │   │   │   ├── aller-light.eot
        │   │   │   ├── aller-light.ttf
        │   │   │   ├── aller-light.woff
        │   │   │   ├── novecento-bold.eot
        │   │   │   ├── novecento-bold.ttf
        │   │   │   └── novecento-bold.woff
        │   │   └── stylesheets
        │   │       └── normalize.css
        │   └── underscore.html
        ├── favicon.ico
        ├── index.html
        ├── package.json
        ├── test
        │   ├── arrays.js
        │   ├── chaining.js
        │   ├── collections.js
        │   ├── functions.js
        │   ├── index.html
        │   ├── objects.js
        │   ├── speed.js
        │   ├── utility.js
        │   └── vendor
        │       ├── jquery.js
        │       ├── jslitmus.js
        │       ├── qunit.css
        │       ├── qunit.js
        │       └── runner.js
        ├── underscore-min.js
        ├── underscore-min.map
        └── underscore.js

60 directories, 384 files
```





## .gitignore
- これをサンプルに
```

# Created by https://www.gitignore.io/api/osx,bower,node

### OSX ###
*.DS_Store
.AppleDouble
.LSOverride

# Icon must end with two \r
Icon
# Thumbnails
._*
# Files that might appear in the root of a volume
.DocumentRevisions-V100
.fseventsd
.Spotlight-V100
.TemporaryItems
.Trashes
.VolumeIcon.icns
.com.apple.timemachine.donotpresent
# Directories potentially created on remote AFP share
.AppleDB
.AppleDesktop
Network Trash Folder
Temporary Items
.apdisk


### Bower ###
bower_components
.bower-cache
.bower-registry
.bower-tmp


### Node ###
# Logs
logs
*.log
npm-debug.log*

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# Directory for instrumented libs generated by jscoverage/JSCover
lib-cov

# Coverage directory used by tools like istanbul
coverage

# nyc test coverage
.nyc_output

# Grunt intermediate storage (http://gruntjs.com/creating-plugins#storing-task-files)
.grunt

# node-waf configuration
.lock-wscript

# Compiled binary addons (http://nodejs.org/api/addons.html)
build/Release

# Dependency directories
node_modules
jspm_packages

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Optional REPL history
.node_repl_history

# Output of 'npm pack'
*.tgz

# Yarn Integrity file
.yarn-integrity


# End of https://www.gitignore.io/api/osx,bower,node
```
