---
title: Minimal MistakesテーマによるJekyllブログのハンズオン
---

## 概要

http://k11i.biz/blog/2016/08/11/starting-jekyll-with-Minimal-Mistakes/
の写経を実行する。ただし、ローカルで unixコマンド, hub, rubyが実行できるとする。

## Minimal Mistakesテーマ

- ゆるふわポートフォリオ的なブログに向いている印象
- ソーシャルボタンが付いている
- 本文の文字は大きめになる

## Jekyllのローカル動作確認

https://mmistakes.github.io/minimal-mistakes/docs/installation/

から [Download Minimal Mistakes Theme] で得た書庫ファイルを解凍する。

そのディレクトリで

```
bundle
```

を行ってから、

```
bundle exec jekyll serve
```

で http://127.0.0.1:4000/ にて動作確認する。

## GitHubにpush

```
mkdcd play-jekyll3
git init
hub create
# 先程のファイル一式をこのディレクトリにコピーしてから
git add .; git commit -m 'update'; git push origin master
```

## GitHub Pagesの有効化

`hub browse` から [Settings] で master ブランチの GitHub Pages を有効にする。
1分ほど待てば、GitHub側でJekyllビルドがなされ、ブログが見られるようになる。

https://kuronat.github.io/play-jekyll3/

## 新規記事の作成(ブラウザ)

`docs/_posts` にある作例にならって、作ってみる。

`hub browse` から [Create New File] より `_posts/2017-11-12-hello-world.md` を作成する。

```
---
title: "世界の始まり"
categories:
  - Edge Case
tags:
  - content
  - css
  - edge case
  - lists
  - markup
---

こんにちは、世界
```

コミットして暫く待つと、ブログ記事として反映されている。

## 新規記事の作成(CLI)

```
git pull origin master
nano _posts/2017-11-12-jekyll-with-minimal-mistakes.md
git add .; git commit -m 'update'; git push origin master
```

(更新されない…と思ったら、ブラウザにキャッシュが残っていただけであった)

## メタデータ解説

- `title:` は記事HTMLの `<title>` タグに対応する
- `categories:` やファイル名の一部は URL を形成する
- `tags:` からタグをつけることができる

その他いろいろ、つけることができる。

## まとめ

- Jekyll + GitHub Pagesは、初期設定をいちどすれば、記事作成はブラウザだけでOK
- Minimal Mistakesテーマは文字がでかくてゆるふわな印象を与える
