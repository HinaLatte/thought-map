# 思考地図採集帳

心の観測、思考の流れ、身体反応、気づき、手当て、ひだまりを入力し、MNP形式のMarkdownを生成するための1枚HTMLツールです。

## 使い方

GitHub Pagesで公開された `index.html` をブラウザで開きます。

1. 各入力欄に観測内容を書きます。
2. 右側のMarkdownプレビューを確認します。
3. `Markdownをコピー` ボタンでMarkdownをコピーするか、`Markdownを保存` ボタンで `.md` ファイルをダウンロードします。
4. 表示されたファイル名候補を使い、`entries/` フォルダにMarkdownファイルを追加します。

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
    index.json
    2026-06-10-map001.md
  prompts/
    整理してもらう.md
  README.md
```

`index.html` はブラウザ内でMarkdownを生成し、コピーまたはダウンロードできます。GitHub API連携は行わないため、ダウンロードした `.md` ファイルは手動で `entries/` に追加します。

## 採集一覧

トップ画面の採集一覧は、`entries/index.json` を読み込んで表示します。GitHub Pagesだけでは `entries/` フォルダ内のファイルを自動列挙できないため、新しいMarkdownファイルを追加したら `entries/index.json` も更新します。

例:

```json
[
  {
    "file": "2026-06-10-map001.md",
    "date": "2026-06-10",
    "title": "最初の思考地図"
  }
]
```

`file` には `entries/` から見たファイル名、`date` には `YYYY-MM-DD`、`title` には一覧に表示するタイトルを書きます。

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
