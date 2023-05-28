---
title: "『Windows10』不要アプリ削除方法まとめ"
date: 2023-05-28T22:47:02+09:00
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
tags: ["WindowsOS", "Shell"]
description: "「追いかけ続ける勇気さえあれば、夢は必ず叶います」"
weight:
cover:
    image: "posts/technology/『Windows10』不要アプリ削除方法まとめ/『Windows10』不要アプリ削除方法まとめ.001.png"
    alt: ""
    caption: ""
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
# ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝🔼編集必要🔼＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
---

## マウスのスクロール方向を変更

下記コマンドは WindowsOS のマウスのスクロール方向を MacOS と同じように変更できます。

最後の数字で方向を設定できます。

Windows10：０

MacOS：１

```shell
Get-ItemProperty HKLM:\SYSTEM\CurrentControlSet\Enum\HID\*\*\Device` Parameters FlipFlopWheel -EA 0 | ForEach-Object { Set-ItemProperty $_.PSPath FlipFlopWheel 1 }
```

