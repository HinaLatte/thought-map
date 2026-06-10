# 思考地図採集帳

心の観測、思考の流れ、身体反応、気づき、手当て、ひだまりを入力し、MNP形式のMarkdownを生成するための1枚HTMLツールです。

## 使い方

GitHub Pagesで公開された `index.html` をブラウザで開きます。

1. 各入力欄に観測内容を書きます。
2. 右側のMarkdownプレビューを確認します。
3. `Markdownをコピー` ボタンでMarkdownをコピーします。
4. 表示されたファイル名候補を使い、`entries/` フォルダにMarkdownファイルとして保存します。

ファイル名の例:

```text
2026-06-10-map001.md
```

## 保存場所

採集したMarkdownは、リポジトリ内の `entries/` フォルダに保存します。

```text
thought-map/
  index.html
  entries/
    .gitkeep
    2026-06-10-map001.md
  prompts/
    整理してもらう.md
  README.md
```

`index.html` には保存機能を持たせていません。ブラウザ内でMarkdownを生成し、コピーした内容を手元で `.md` ファイルとして作成してから、`entries/` に追加する運用です。

## GitHub Pages

このリポジトリは、GitHub Pagesで `index.html` を公開する前提です。

GitHub Pagesの設定例:

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

公開後は、リポジトリ直下の `index.html` が入力画面として表示されます。

## 生成されるMarkdown形式

```markdown
# map 001

date: YYYY-MM-DD
title: 入力タイトル

[event]
...

[path]
...

[body]
...

[feeling]
...

[fact]
...

[insight]
...

[care]
...

[sunlight]
...
```

## promptsについて

`prompts/` フォルダには、保存した採集メモをあとから整理したり、読み返しやすい形に整えたりするためのプロンプトを置きます。
