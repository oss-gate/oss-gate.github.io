# oss-gate.github.io

OSS GateのWebサイトのリポジトリ。

https://oss-gate.github.io/

## 仕組み
GitHub pages（jekyll）を使用。markdownファイルとhtmlファイルを編集して、リポジトリにアップすると、GitHubがWebページに変換してくれる。

テーマには、defaultのminimaを使用。https://github.com/jekyll/minima

cssをsassで少し足している。

## ローカル環境でのプレビュー

```shell
$ bundle install --path vendor/
$ bundle exec jekyll serve --drafts --livereload --incremental --force-polling
```

* `--drafts` は下書き状態の記事を強制的にレンダリングするために必要。
* `--force-polling` は[Windows 10でのWSL1での既知の不具合](https://talk.jekyllrb.com/t/jekyll-serve-hangs-under-wsl-requires-restart-to-kill-process/5424)の回避に必要。それ以外の環境では省略してもよい。


## ICONについて

Font Awesome licensed under SIL OFL 1.1 http://fontawesome.io/

## ライセンスについて

Copyright 2015-2020 OSS Gate

このサイトのライセンスは [Creative Commons Attribution-ShareAlike 4.0 International License][cc-by-sa] です。

[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
