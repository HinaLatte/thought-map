# 思考地図採集帳

心の観測、思考の流れ、身体反応、気づき、手当て、ひだまりを入力し、MNP形式のMarkdownを生成するための1枚HTMLツールです。

## 使い方

GitHub Pagesで公開された `index.html` をブラウザで開きます。  
https://hinalatte.github.io/thought-map/

1. 各入力欄に観測内容を書きます。
2. 右側のMarkdownプレビューを確認します。
3. `Markdownをコピー` ボタンでMarkdownをコピーするか、`Markdownを保存` ボタンで `.md` ファイルをダウンロードします。
4. GitHub Pages上では、`Issueとして保存` ボタンからGitHub Issueを作成できます。
5. `thought-map-entry` ラベル付きのIssueが作成されると、GitHub Actionsが `entries/` にMarkdownを保存します。

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

## Issue経由の保存

GitHub Pagesの入力画面で `Issueとして保存` を押すと、GitHubの新規Issue作成画面が開きます。

- Issue title: ファイル名候補
- Issue body: 生成されたMNP Markdown
- label: `thought-map-entry`

Issueを投稿すると、`.github/workflows/save-entry.yml` が実行されます。ワークフローはIssue本文を `entries/*.md` として保存し、`entries/index.json` を更新してcommit & pushします。保存後、Issueにコメントしてcloseします。

同じファイル名がすでに `entries/` に存在する場合は上書きしません。Issueへエラーコメントを残し、Issueはcloseしません。

事前にGitHubリポジトリで `thought-map-entry` ラベルを作成しておいてください。

## GitHub Actionsの権限

Issue経由で保存するには、GitHub Actionsがリポジトリへ書き込める必要があります。

GitHubの設定で次を有効にします。

```text
Settings > Actions > General > Workflow permissions
Read and write permissions
```

ワークフロー側では次の権限を使います。

```yaml
permissions:
  contents: write
  issues: write
```

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
