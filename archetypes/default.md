---
title: "{{ replace .Name "-" " " | title }}" #　タイトル
tags: ["領域", "言語", "技術"]
date: {{ .Date }} # 作成日付
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
searchHidden: trus # 検索可能
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