---
title: "『Python』Python のインストール"
date: 2023-05-19T22:44:31+09:00
author: ["JOJO"]
hidemeta: false
draft: true
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
tags: ["Backend", "Python", "Homebrew"]
description: "「追いかけ続ける勇気さえあれば、夢は必ず叶います」"
weight:
cover:
    image: "default-cover/default-cover.png"
    alt: ""
    caption: ""
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
# ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝🔼編集必要🔼＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
---

## Homebrewでインストール

macOS ならHomebrewを利用してPythonを便利インストールできますが、Pythonのバージョン

```
~ ➤ brew search python                                                        git:master*
==> Formulae
app-engine-python             python-lsp-server             python@3.11
boost-python3                 python-markdown               python@3.7
bpython                       python-tabulate               python@3.8
ipython                       python-tk@3.10                python@3.9
micropython                   python-tk@3.11                reorder-python-imports
ptpython                      python-tk@3.9                 wxpython
python-build                  python-typing-extensions      pythran
python-gdbm@3.11              python-yq                     jython
python-launcher               python@3.10                   cython

==> Casks
mysql-connector-python
```

```
~ ➤ brew info python                                                          git:master*
==> python@3.11: stable 3.11.3 (bottled)
Interpreted, interactive, object-oriented programming language
https://www.python.org/
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/python@3.11.rb
License: Python-2.0
==> Dependencies
Build: pkg-config ✘
Required: mpdecimal ✔, openssl@1.1 ✔, sqlite ✘, xz ✔
==> Caveats
Python has been installed as
  /opt/homebrew/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
  /opt/homebrew/opt/python@3.11/libexec/bin

You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /opt/homebrew/lib/python3.11/site-packages

tkinter is no longer included with this formula, but it is available separately:
  brew install python-tk@3.11

gdbm (`dbm.gnu`) is no longer included in this formula, but it is available separately:
  brew install python-gdbm@3.11
`dbm.ndbm` changed database backends in Homebrew Python 3.11.
If you need to read a database from a previous Homebrew Python created via `dbm.ndbm`,
you'll need to read your database using the older version of Homebrew Python and convert to another format.
`dbm` still defaults to `dbm.gnu` when it is installed.

For more information about Homebrew and Python, see: https://docs.brew.sh/Homebrew-and-Python
==> Analytics
install: 3,434 (30 days), 99,655 (90 days), 1,684,653 (365 days)
install-on-request: 926 (30 days), 23,145 (90 days), 193,171 (365 days)
build-error: 6 (30 days)
~ ➤ brew install python                                                       git:master*
==> Fetching dependencies for python@3.11: sqlite
==> Fetching sqlite
==> Downloading https://ghcr.io/v2/homebrew/core/sqlite/manifests/3.42.0
################################################################################### 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/sqlite/blobs/sha256:c9b11a8dd4fd8996ba240
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sha256:c9b11
################################################################################### 100.0%
==> Fetching python@3.11
==> Downloading https://ghcr.io/v2/homebrew/core/python/3.11/manifests/3.11.3
Already downloaded: /Users/admin/Library/Caches/Homebrew/downloads/6c839300228ac3383f7ebf7bcc20456ca127918286a03a9f3d41f00767e320d0--python@3.11-3.11.3.bottle_manifest.json
==> Downloading https://ghcr.io/v2/homebrew/core/python/3.11/blobs/sha256:a6f7dd653b6c5904
Already downloaded: /Users/admin/Library/Caches/Homebrew/downloads/13442ac96116dd964aeed18feaeb64d15f66235eb6c34abe73d1efebf6000713--python@3.11--3.11.3.arm64_ventura.bottle.tar.gz
==> Installing dependencies for python@3.11: sqlite
==> Installing python@3.11 dependency: sqlite
==> Pouring sqlite--3.42.0.arm64_ventura.bottle.tar.gz
🍺  /opt/homebrew/Cellar/sqlite/3.42.0: 11 files, 4.5MB
==> Installing python@3.11
==> Pouring python@3.11--3.11.3.arm64_ventura.bottle.tar.gz
==> /opt/homebrew/Cellar/python@3.11/3.11.3/bin/python3.11 -m ensurepip
==> /opt/homebrew/Cellar/python@3.11/3.11.3/bin/python3.11 -m pip install -v --no-deps --n
==> Caveats
Python has been installed as
  /opt/homebrew/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
  /opt/homebrew/opt/python@3.11/libexec/bin

You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /opt/homebrew/lib/python3.11/site-packages

tkinter is no longer included with this formula, but it is available separately:
  brew install python-tk@3.11

gdbm (`dbm.gnu`) is no longer included in this formula, but it is available separately:
  brew install python-gdbm@3.11
`dbm.ndbm` changed database backends in Homebrew Python 3.11.
If you need to read a database from a previous Homebrew Python created via `dbm.ndbm`,
you'll need to read your database using the older version of Homebrew Python and convert to another format.
`dbm` still defaults to `dbm.gnu` when it is installed.

For more information about Homebrew and Python, see: https://docs.brew.sh/Homebrew-and-Python
==> Summary
🍺  /opt/homebrew/Cellar/python@3.11/3.11.3: 3,178 files, 62.1MB
==> Running `brew cleanup python@3.11`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> Caveats
==> python@3.11
Python has been installed as
  /opt/homebrew/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
  /opt/homebrew/opt/python@3.11/libexec/bin

You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /opt/homebrew/lib/python3.11/site-packages

tkinter is no longer included with this formula, but it is available separately:
  brew install python-tk@3.11

gdbm (`dbm.gnu`) is no longer included in this formula, but it is available separately:
  brew install python-gdbm@3.11
`dbm.ndbm` changed database backends in Homebrew Python 3.11.
If you need to read a database from a previous Homebrew Python created via `dbm.ndbm`,
you'll need to read your database using the older version of Homebrew Python and convert to another format.
`dbm` still defaults to `dbm.gnu` when it is installed.

For more information about Homebrew and Python, see: https://docs.brew.sh/Homebrew-and-Python

```

