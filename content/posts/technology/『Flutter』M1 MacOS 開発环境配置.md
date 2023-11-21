---
title: "『Flutter』M1 MacOS 開発环境配置"
date: 2023-05-29T22:45:49+09:00
author: ["JOJO"]
hidemeta: false
draft: false
UseHugoToc: true
showToc: true
TocOpen: true
showbreadcrumbs: true
comments: true
canonicalURL: "https://zhangpeng-system.github.io/blog/"
searchHidden: true
hideSummary: false
disableHLJS: false
disableShare: false
ShowReadingTime: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
# ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝🔽編集必要🔽＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
tags: ["Flutter", "Dart", "Macbook"]
description: "「追いかけ続ける勇気さえあれば、夢は必ず叶います」"
weight:
cover:
    image: "posts/technology/『Flutter』M1 MacOS 開発环境配置/『Flutter』M1 MacOS 開発环境配置.001.png"
    alt: ""
    caption: ""
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
# ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝🔼編集必要🔼＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
---

# はじめに

- Flutter 公式からも環境設定の説明を用意していますが、実際に着手してみると、初めてなので色々トラブルが発生しました。
- 本記事では 、私が踏んだ落穴を経験として、M1 Macbook をターゲットに導入中の注意点と導入順番を改善しました。
- M1 Macbook であれば、公式より本記事の方が詳しくてわかりやすいと思っています。

# Rosetta 2（SUDO命令）

- Apple Silicon Mac に Flutter を 導入する場合 Rosetta（ロゼッタ）が必要です。
  ターミナルを開き、下記のコマンドで Rosetta 2 を導入します。

> Rosetta（ロゼッタ）とは ？
>
> Rosetta（ロゼッタ）は、特定のアーキテクチャのプログラムコードを持つバイナリを、別のアーキテクチャに適宜変換 (en:Dynamic recompilation) することでバイナリの互換性を維持する Apple の技術。

```
sudo softwareupdate --install-rosetta --agree-to-licensea
```

> sudo 命令を実行するには Mac のパスワードが要求されますが、入力して実行を続きます。

```
~ % sudo softwareupdate --install-rosetta --agree-to-licensea
Password:
softwareupdate: unrecognized option `--agree-to-licensea'
usage: softwareupdate <cmd> [<args> ...]

** Manage Updates:
	-l | --list		List all appropriate update labels (options:  --no-scan, --product-types)
	-d | --download		Download Onlyƒ
	-i | --install		Instal
		<label> ...	specific updates
		-a | --all		All appropriate updates
		-R | --restart		Automatically restart (or shut down) if required to complete installation.
		-r | --recommended	Only recommended updates
		     --os-only	Only OS updates
		     --safari-only	Only Safari updates
		     --stdinpass	Password to authenticate as an owner. Apple Silicon only.
		     --user	Local username to authenticate as an owner. Apple Silicon only.
	--list-full-installers		List the available macOS Installers
	--fetch-full-installer		Install the latest recommended macOS Installer
		--full-installer-version	The version of macOS to install. Ex: --full-installer-version 10.15
	--install-rosetta	Install Rosetta 2
	--background		Trigger a background scan and update operation

** Other Tools:
	--dump-state		Log the internal state of the SU daemon to /var/log/install.log
	--evaluate-products	Evaluate a list of product keys specified by the --products option 
	--history		Show the install history.  By default, only displays updates installed by softwareupdate.  

** Options:
	--no-scan		Do not scan when listing or installing updates (use available updates previously scanned)
	--product-types <type>		Limit a scan to a particular product type only - ignoring all others
		Ex:  --product-types macOS  || --product-types macOS,Safari 
	--products		A comma-separated (no spaces) list of product keys to operate on. 
	--force			Force an operation to complete.  Use with --background to trigger a background scan regardless of "Automatically check" pref 
	--agree-to-license		Agree to the software license agreement without user interaction.

	--verbose		Enable verbose output
	--help			Print this help

~ % 
```

# Xcode（App Store）

- Apple Store を開き、`Xcode`と言うソフトウエアをインストールします。

> なぜ`Xcode`を導入しますか？
>
> 主に iOS シミュレーターを使用するため、いわば iOS 用の Flutter アプリを開発するためです。
>
> 後は Xcode コマンド ライン ツール を使用するためです。
>
> Xcode と Xcode コマンド ライン ツールの関係や利用方法についてはここで展開しません。

![image-20230126225646874.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/c5010ec9-d469-b74c-5fbf-15ecbf477e31.png)


- ターミナルを開き、下記コマンドで Xcode コマンド ライン ツールを最新にします。

> sudo 命令はパスワードが要求されるので、入力してください。
>
> この設定が実行されたら、何も出ませんのが正常です。心配しないでください。

```
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
```

- 最新バージュンへの自動化設定を下記コマンドで設定します。

```
sudo xcodebuild -runFirstLaunch
```

# Cocoapods（brew）

**ちょっと大事なことをここで：**

> Uinx like（macOS） で開発環境の設定やソフトウエアの管理を便利にできるのが `Homebrew`を使用するのが定番です。

> 本記事の環境設定も、面倒なパス設定をスッキプするために`Homebrew`を利用しています。

> 簡単な利用方法は10分ですぐ出来ますので、`Homebrew`の使用解説は[こちら](https://qiita.com/zhangpeng/items/28fcec7539addd523f26)またはネット上の記事を参照してください。

- macOS デスクトップ開発とプラグインの使用は Cocoapods が必要となります。

> Cocoapodsとは
>
> CocoaPods は、Swift および Objective-C プロジェクトの依存関係マネージャーです。93,000 以上のライブラリがあり、300 万以上のアプリで使用されています。CocoaPods は、プロジェクトをエレガントにスケーリングするのに役立ちます。

- ターミナルを開き、下記のコマンドで Cocoapods を導入します。

```
brew install cocoapods
```

```
~ % brew install cocoapods
Warning: Treating cocoapods as a formula. For the cask, use homebrew/cask/cocoapods
==> Fetching dependencies for cocoapods: libyaml, ca-certificates, openssl@1.1, readline and ruby
==> Fetching libyaml
＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝長い一部を省略します＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
==> Installing cocoapods
==> Pouring cocoapods--1.11.3_1.arm64_ventura.bottle.1.tar.gz
🍺  /opt/homebrew/Cellar/cocoapods/1.11.3_1: 13,476 files, 27.9MB
==> Running `brew cleanup cocoapods`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
~ % 
```

> 気づいたかもしれない、Cocoapods 以外のソフトウエアもいくつ導入されています。
>
> それは Cocoapods を利用できるための依存ソフトウエアです、`Homebrew`を使っているので、Cocoapods とその依存ソフトウエアを容易に管理できます。

![image-20230126233605059.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/1e5dd5c9-2461-0c45-3a50-20c930070cfa.png)

# Flutter SDK（brew）

- ターミナルを開き、下記のコマンドで Flutter SDK を導入します。

```
brew install flutter
```

- 🍺  flutter was successfully installed!

```
~ % brew install flutter
Running `brew update --auto-update`...
==> Auto-updated Homebrew!
Updated 2 taps (homebrew/core and homebrew/cask).

==> Downloading https://storage.googleapis.com/flutter_infra_release/releases/st
Already downloaded: /Users/admin/Library/Caches/Homebrew/downloads/18fd0ad2115d4c8b910546eee9d8df2c41d37b327355bd47dca81bbf52227d37--flutter_macos_arm64_3.3.10-stable.zip
==> Installing Cask flutter
==> Linking Binary 'dart' to '/opt/homebrew/bin/dart'
==> Linking Binary 'flutter' to '/opt/homebrew/bin/flutter'
🍺  flutter was successfully installed!
```

> コマンド一行で導入完了！

# Java（brew）

- Android 用の Flutter アプリを開発するため Java が必要です。
  ターミナルを開き、下記のコマンドで Open JDK、いわゆる Java を導入します。

```
brew install openjdk
```

```
~ % brew install openjdk
==> Fetching dependencies for openjdk: giflib, libpng, freetype, fontconfig, pcre2, gettext, glib, xorgproto, libxau, libxdmcp, libxcb, libx11, libxext, libxrender, lzo, pixman, cairo, graphite2, icu4c, harfbuzz, jpeg-turbo, lz4, xz, zstd, libtiff and little-cms2
==> Fetching giflib
＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝長い一部を省略します＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝

If you need to have openjdk first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' >> ~/.zshrc

For compilers to find openjdk you may need to set:
  export CPPFLAGS="-I/opt/homebrew/opt/openjdk/include"

~ % sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
Password:
~ % echo 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' >> ~/.zshrc
~ % export CPPFLAGS="-I/opt/homebrew/opt/openjdk/include"
~ % 
```

- Homebrew はいつも最新なバージョンをインストールします。
  何も出来ませんが、一度`java -version`でバージュンを確認して安心します。

```
~ % java -version
openjdk version "19.0.1" 2022-10-18
OpenJDK Runtime Environment Homebrew (build 19.0.1)
OpenJDK 64-Bit Server VM Homebrew (build 19.0.1, mixed mode, sharing)
~ % 
```

# Android Studio（brew）

- ターミナルを開き、下記のコマンドで Android Studio 導入します。

```
brew install android-studio
```

- インストール完了したら、`Android Studio`を開きます。

```
==> Installing Cask android-studio
==> Moving App 'Android Studio.app' to '/Applications/Android Studio.app'
🍺  android-studio was successfully installed!
```

![スクリーンショット 2023-02-01 20.01.55.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/7103607c-f305-50c9-e4ec-d503d36688db.png)


- Plugin で Flutter（ Dart） をダウンロードします。

![image-20230201200656211.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/ced443b0-70d8-5f4f-2940-d04f2d838728.png)


- `All settings`を開き、下記場所で`Android-SDK command line tools(latest)`をダウンロードします。

![スクリーンショット 2023-02-01 20.08.28.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/ebcabedf-da7d-a8f7-3518-c8bc0ef120f7.png)
![image-20230201201735534.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/e19e6d63-f216-d1d7-be6c-7f6b6d3ed2a9.png)



- 次は謎のエラー`✗ Unable to find bundled Java version.`を解決するてため、下記の手順を行います。

> 原因不明で`Android studio`の名前が`jre`のフォルダが`jbr`になっています。これを修正します。	

- アイコンを右クリックして、`パッケージの内容を表示`を選択します。

![image-20230201203628765.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/ce63de60-a0d7-8bc0-7551-f5159103c354.png)


- 新規フォルダで名前を`jre`にします。

![image-20230201203852004.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/2d1c3d81-01a3-2c0a-9dce-c90fff62f6ed.png)


- `jbr`の中身を`jre`フォルダの中にコピペします。

![image-20230201204236264.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/3b4f4d45-89b3-f6f2-e377-e09dc8fe84df.png)


- ターミナルを開き、下記のコマンドで Android ライセンス規約をYes（同意）しながら導入します。

```
$ flutter doctor --android-licenses
```

> 写真を撮り忘れました。。。

# Hello World ! （Flutter）

>  早速Flutter DEMOを一つ立ち上げましょう。

- `New Flutter Project`を選択します。

![image-20230201204614005.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/0dbd0c15-e19c-eb1c-9850-f624eec5f499.png)


- 下記のパスに Homebrew でダウンロードした Flutter を見つけて選択します。

```
/opt/homebrew/Caskroom/flutter/3.3.10/flutter
```

![image-20230201210229402.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/8a6bd362-3474-ff07-4039-3de16ab54276.png)


- プロジェクトの名前を入力して、`Create`を選択します。

![image-20230201205832811.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/e563fbaa-311b-6822-e5d3-858aa898ec52.png)


- これで Flutter のプロジェクトが作成できました。

![image-20230201205916568.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/b639b4d4-ed99-9ff5-94a8-8af1e4d3c947.png)


- Chrome でプロジェクトを実行します。

![image-20230201210814903.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/c624bf27-89d1-2891-dba5-5a66bff0b0fa.png)


# 終わりに

ほぼゼロから M1 Macbook の Flutter 導入方法を説明しました。ご参考になればうれしいと思います。

わからない事や補充のところがあれば、コメントで遠慮なくお願いします。