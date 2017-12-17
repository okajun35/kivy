KivyのTextInputでIMEを使用するためのコード
====


+ 2017/12/17の本家のバージョンをもとにしています
+ [Add textedit event for text editing by IME #5109](https://github.com/kivy/kivy/pull/5109)の要素をマージしています
+ このKivyの内容をインストールすることで[kivy_textedit_sample](https://github.com/Adachinski/kivy_textedit_sample)を使用することができます。

インストール方法
-------
kivy-textime.zipをダウンロードして保存してください。

検証環境はPython3.6でOSはwindows10の６４bit環境です。

※未検証ですが恐らくmac環境でも動作すると思います。

[Use development Kivy(Kivyの開発バージョンを使用する)](https://pyky.github.io/kivy-doc-ja/installation/installation-windows.html#use-development-kivy)のやり方を基本にしています。


1. [Visual C++ 2015 BuildTools](http://landinghub.visualstudio.com/visual-cpp-build-tools)をダウンロードしてインストールします。

2. 環境変数PathにインストールしたBuildToolsのパスを通します。例は以下
```
C:\Program Files\Microsoft VS Code\bin
```
3. コマンドプロンプト[cmd]を立ち上げます。

4. 環境変数を設定します

```
set USE_SDL2=1
set USE_GSTREAMER=1
```
※PowerShellだと以下になります　
```
$env:USE_SDL2 = 1
$env:USE_GSTREAMER = 1
```

5. PiPとwhileを最新にします

```
python -m pip install --upgrade pip wheel setuptools
```

6. 依存関係をインストールします

```
python -m pip install cython docutils pygments pypiwin32 kivy.deps.sdl2 kivy.deps.glew kivy.deps.gstreamer kivy.deps.glew_dev kivy.deps.sdl2_dev kivy.deps.gstreamer_dev
```

7. Kivyのビルドをします
zipを展開した、kivy-masterの直下に移動してビルドします

```
python -m pip install .
```

8.Kivyを実行します
[kivy_textedit_sample](https://github.com/Adachinski/kivy_textedit_sample)を実行(main.py)して起動時のログを確認してください。

※TextとWindowのでProviderがSDL2になっていることを必ず確認してください。Pygameが表示されている場合は環境変数の設定がおかしいので見直してください。

```
[INFO   ] [Text        ] Provider: sdl2
[INFO   ] [OSC         ] using <thread> for socket
[INFO   ] [Window      ] Provider: sdl2

```

この状態で実行すると、TextinputIMEの隣のラベルに全角（日本語入力）で未確定の文字（Enterを入力する前）の文字が表示されます。

注意事項としては、スペースキーを押して変換はできますが変換候補の一覧は表示されません。また入力ですが一度に入力できる文字数は最大１５文字までです。

Kivyで日本語入力ができない問題の詳しい説明は[リンク先の記事](https://qiita.com/dario_okazaki/items/8c6953166b336e83e417)を見てみてください。




------------------------------------------
Kivy
====

<img align="right" height="256" src="https://raw.githubusercontent.com/kivy/kivy/master/kivy/data/logo/kivy-icon-256.png"/>

Innovative user interfaces made easy.

Kivy is an open source, cross-platform [Python](https://www.python.org)
framework for the development of applications that make use of innovative,
multi-touch user interfaces.
The aim is to allow for quick and easy interaction design and rapid prototyping
whilst making your code reusable and deployable.

Kivy is written in Python and [Cython](http://cython.org/), based on OpenGL ES
2, supports various input devices and has an extensive widget library. With the
same codebase, you can target Windows, OS X, Linux, Android and iOS. All Kivy
widgets are built with multitouch support.

Kivy is MIT licensed, actively developed by a great community and is supported
by many projects managed by the [Kivy Organization](https://kivy.org/#organization).

[![Coverage Status](https://coveralls.io/repos/kivy/kivy/badge.svg?branch=master)](https://coveralls.io/r/kivy/kivy?branch=master)
[![Build Status](https://travis-ci.org/kivy/kivy.svg?branch=master)](https://travis-ci.org/kivy/kivy)
[![Build status](https://ci.appveyor.com/api/projects/status/sqc46n4a3bq2gj1s/branch/master?svg=true)](https://ci.appveyor.com/project/KivyOrg/kivy/branch/master)
[![Bountysource](https://www.bountysource.com/badge/tracker?tracker_id=42681)](https://www.bountysource.com/trackers/42681-kivy?utm_source=42681&utm_medium=shield&utm_campaign=TRACKER_BADGE)

Installation, Documentation and Examples
----------------------------------------

Extensive installation instructions as well as tutorials and general
documentation, including an API reference, can be found at https://kivy.org/docs.
A [PDF version](https://media.readthedocs.org/pdf/kivy/latest/kivy.pdf) is also available.

Kivy ships with many examples which can be found in the `examples` folder.

Support
-------

If you need assistance, you can ask for help on our mailing list:

* User Group : https://groups.google.com/group/kivy-users
* Email      : kivy-users@googlegroups.com

We also have an IRC channel:

* Server     : irc.freenode.net
* Port       : 6667, 6697 (SSL only)
* Channel    : #kivy
* Web client : [WebChat](https://webchat.freenode.net/?nick=kvuser.&channels=kivy&uio=d4)

Contributing
------------

We love pull requests and discussing novel ideas. Check out our
[contribution guide](https://kivy.org/docs/contribute.html) and
feel free to improve Kivy.

The following mailing list and IRC channel are used exclusively for
discussions about developing the Kivy framework and its sister projects:

* Dev Group : https://groups.google.com/group/kivy-dev
* Email     : kivy-dev@googlegroups.com

IRC channel:

* Server     : irc.freenode.net
* Port       : 6667, 6697 (SSL only)
* Channel    : #kivy-dev
* Web client : [WebChat](https://webchat.freenode.net/?nick=kvuser.&channels=kivy-dev&uio=d4)

Sister projects
---------------

- [Buildozer](https://github.com/kivy/buildozer): generic Python packager
  for Android and iOS.
- [Plyer](https://github.com/kivy/plyer): platform-independent Python wrapper
  for platform-dependent APIs.
- [Pyjnius](https://github.com/kivy/pyjnius): dynamic access to the Java/Android
  API from Python.
- [Pyobjus](https://github.com/kivy/pyobjus): dynamic access to the
  Objective-C/iOS API from Python.
- [Python for Android](https://github.com/kivy/python-for-android): toolchain
  for building and packaging Python applications for Android.
- [Kivy iOS](https://github.com/kivy/kivy-ios): toolchain for building and
  packaging Kivy applications for iOS.
- [Audiostream](https://github.com/kivy/audiostream): library for direct access
  to the microphone and speaker.
- [Kivy Designer](https://github.com/kivy/kivy-designer): UI designer for Kivy.
- [KivEnt](https://github.com/kivy/kivent): entity-based game engine for Kivy.
- [Garden](https://github.com/kivy-garden): widgets and libraries created and
  maintained by users.

Licenses
--------

- Kivy is released under the terms of the MIT License. Please refer to the
  LICENSE file.
- The provided fonts Roboto and Roboto Mono are licensed and
  distributed under the terms of the
  [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
  The DejaVuSans (used for the virtual keyboard) license can be viewed
  [here](https://github.com/dejavu-fonts/dejavu-fonts/blob/master/LICENSE).
- The current UI design has been adapted from Moblintouch theme's SVGs
  and is licensed under the terms of the
  [LGPLv2.1](https://www.gnu.org/licenses/old-licenses/lgpl-2.1).
