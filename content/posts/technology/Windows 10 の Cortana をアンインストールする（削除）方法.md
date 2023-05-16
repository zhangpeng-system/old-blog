---
title: "Windows 10 の Cortana をアンインストールする（削除）方法" #　タイトル
tags: ["領域", "言語", "技術"]
date: 2023-05-17T00:26:35+09:00 # 作成日付
author: ["JOJO"] # 作者
weight: # 表示順番
draft: false # 下書き
showToc: true # 目次
TocOpen: true # 目次の自動展開
hidemeta: false # ブログメッセージの表示
comments: true #　コメント
# description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false # Fooderのシェアボタンの表示
disableHLJS: false
hideSummary: false
searchHidden: false # 検索可能
ShowReadingTime: true #　閲覧予測時間
showbreadcrumbs: true #　目次のパス表示
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "default-cover/default-cover.png" # 画像パス：posts/life/ブログファイル同名.png
    alt: "" # 画像キーワード
    caption: "" # 画像説明(画像下部)
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# アンインストール手順

- Windows PowerShellを管理者権限で実行します。

![](https://storage.googleapis.com/zenn-user-upload/9c59532fb185-20230114.png)

- 下記のコマンドをコピペして実行します。

```shell
Get-AppxPackage -allusers Microsoft.549981C3F5F10 | Remove-AppxPackage
```

- 実行完了↓

![](https://storage.googleapis.com/zenn-user-upload/8610ee2d8db2-20230114.png)

- ctrl + C で Cortana を起動して見ると、何も出てきません、これで削除はできました。

