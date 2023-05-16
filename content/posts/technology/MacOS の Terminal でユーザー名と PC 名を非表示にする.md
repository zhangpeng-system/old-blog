---
title: "MacOS の Terminal でユーザー名と PC 名を非表示にする" #　タイトル
tags: ["Terminal", "Shell", "zsh"]
date: 2023-05-17T00:17:50+09:00 # 作成日付
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
    alt: "" # 画像説明
    caption: "" # 画像説明(画像下部)
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
## シンプルなターミナル画面

> Macbook に標準で付属している UNIX 端末エミュレータ「ターミナル」は便利で、エンジンニアにとって、多分一番よく見る画面です。ターミナル自体のデザインはシンプルでとても素敵と思っていますが、ユーザー名とPC名が毎回表示されるのは不便と思っています。

![スクリーンショット 2023-01-13 18.59.06.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/b1f17c3e-2474-b3db-8a9f-83be1bedcd67.png)

- ユーザー名とPC名が表示されている状態です。

![元の画面.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/95faa8bc-8361-625b-108c-39d764a25d28.png)

- ユーザー名と PC 名を隠して見やすくなりました。

![image-20230113201810249.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/f8f75f67-427a-8dec-97bf-9b185246a88e.png)


## 設定方法

- まずは下記コマンドを入力して、今使用している Shell を確認します。筆者の Macbook は Ventura 13.1 を使っていますので、zsh です。

```shell
echo $SHELL
```

![image-20230113192033159.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/c114bea1-2ddc-04d9-8ed4-37861cb318da.png)

- zsh の設定ファイルをVimで開きます。

```shell
vim /etc/zshrc
```

![image-20230113193237987.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/7de4e174-c0fe-eb3d-eea3-e2a01ed0adf2.png)

- 実行したら下記の zshrc ファイルの中身が表示されます。

![image-20230113193351193.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/ab82a4ba-3ded-92a3-b9a3-0162f27bf986.png)

- 下まで移動すると、`# Default prompt`と言う項目が出てきます。

![image-20230113193534128.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/7803c07b-4b67-6ddf-0ff5-bfa3d140c266.png)

- ユーザー名とPC名を隠すには、ここの`nとm`を削除します。

```shell
PS1 : 表示するスタイル
n   : ユーザー名
m   : PC名
```

- 「i」を押して挿入モードに入ります。元の設定をコメントアウトして下記の一行を追加します。

```
PS1="%1~ %# "
```

> 設定ファイルは readonly ですので、一度警告が出ますが無視して編集を続きます。

![image-20230113195806281.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/fd9ce999-c682-d1d7-bd1d-9b81faa2d5fa.png)

- 「esc」を押して挿入モードからノーマルモードへ切り替えます。sudu 命令で変更を保存します。

> 一度パソコンのパスワードが要求されます。自分のパスワードを入力してください。

![スクリーンショット 2023-01-13 20.06.52.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/661a4f68-5ca5-d065-5f81-087851a475df.png)

- 緑色の警告を無視して、続いて下記コマンドを入力して強制的Vimを閉じます。こうやって上書きができました。

```shell
:q!
```

![image-20230113200934129.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/8007ba3b-44f0-b5ba-cd38-90f65d3882f3.png)


- ターミナルを再起動して、ユーザー名とPC名がなくなりました。

![image-20230113201810249.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3076318/fc4d42b2-bc1f-ac2d-ec11-0f8ed54961f2.png)

## 最後

:smiley:ターミナルがすっきりになる事で気持ちいいだけではなく、色んな作業の効率向上にも繋がります。この記事を参考して皆さんが楽しみにしていただければと思っています。
