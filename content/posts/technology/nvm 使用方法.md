---
title: "Nvm 使用方法"
date: 2023-08-20T18:01:56+09:00
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
tags: ["Web", "nvm"]
description: "「追いかけ続ける勇気さえあれば、夢は必ず叶います」"
weight:
cover:
    image: "posts/technology/nvm 使用方法/nvm 使用方法.001.png"
    alt: ""
    caption: ""
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
# ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝🔼編集必要🔼＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
---

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/23aa843b-d389-00cb-fb3a-494deb419e1f.png)

# 概念説明

## nvm

node Version Manager、省略してnvmと呼びます。nodeのバージュン管理ツールです。

nvmを利用する事で、任意バージュンのnodeを簡単にインストール、削除、切り替わって使用や設定ができます。

例えば、Aにnode12を使わせて、Bにnode14を使います。

## node

node.js、省略してnodeとも言います。

Chrome の V8 エンジンで動作する JavaScript 環境です。オープンソースかつ高性能で JavaScript 環境 中の TOP です。

## npm

node Package Manager、またはnpmとも言います。nodeのパッケージ管理システムです。

簡単に説明すると、App Storeみたいなものです。他の人が開発したnode.jsのツールやパッケージをインストールしたり管理ができます。

npmはnode.jsと梱包されています。node.jsをインストールしたら、対応するバージュンのnpmも一緒にインストールされます。

## まとめ

- nvm は node.js のバージュン管理ツールです。
- npm は node.js のパッケージ管理ツールです。

# インストール

## Homebrew

macOS では homebrew を利用して一行のコマンドだけでインストールできます。

```
brew install nvm	
```

# 使用方法

- node.js の最新LTSバージュンをインストール

```
nvm install stable
```
![image-20230210001927107.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/b69c0cce-9d87-d616-b412-253801825f31.png)

![image-20230210001927107](./image-20230210001927107.png)

- node.js の指定バージュンをインストール

```
nvm install version
```
![image-20230210003516932.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/7178b183-c4a6-2a6f-e9ca-0e35bd79e49b.png)

- node.js の指定バージュンを削除

```
nvm uninstall version
```



- node.js のデフォルトバージュンをセット

```
nvm alias defualt version
```
![image-20230210003941353.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/bb30cd9c-c69e-db92-1c6c-463304157ca9.png)


- node.js の指定バージュンを使用

```
nvm use version
```
![image-20230210003818228.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/2aabcaf1-714d-6471-9bda-8466351bdca9.png)


- インストールした node.js を確認

```
nvm list
```
![image-20230210003706473.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/0f601d92-b9af-093d-c5db-7c7824174dce.png)


- 今使っている node.js のバージュンを確認

```
nvm current
```
![image-20230210004140815.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/87d0b107-b2da-51f4-4097-6dcb782bdba0.png)
