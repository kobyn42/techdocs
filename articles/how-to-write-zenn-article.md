---
title: "Zennの記事の書き方"
emoji: "🤖"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Zenn"]
published: true
---
# 初期設定
Github上で連携するリポジトリをあらかじめ作成しておき、Zennと連携をする。

ローカル上で以下のコマンドを実行する。

```bash
npm init --yes
npm install zenn-cli
npx zenn init
```


# 記事の作成
## 新規作成
以下のコマンドで記事が作成される。
ランダムなslugが付与され、Markdownのファイル名もslugになり管理が煩雑になるので、`slug`オプションでスラッグを指定する。

```bash
npx zenn new:article --slug 記事のスラッグ
```

## 画像ファイルの配置
画像ファイルを配置したい場合は`images`ディレクトリ以下に配置して、`/images/`から始まる絶対パスを指定する必要がある。

## プレビュー
以下のコマンドでプレビューができる。

```bash
npx zenn preview
```

# 記事の投稿
MarkdownのファイルをGithubにpushすると、Zennに記事が投稿される。
ただし、`published: false`となっている記事は下書きになるので、投稿したい記事は`published: true`にする。

# VSCodeの設定
新規記事作成、プレビューはよく使うと思うので、VSCodeのタスクの設定をしておくと便利。

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "New Article",
            "type": "shell",
            "command": "npx zenn new:article --slug ${input:slug} --type idea --emoji 🤖",
            "problemMatcher": [],
        },
        {
            "label": "Preview",
            "type": "shell",
            "command": "npx zenn preview",
            "problemMatcher": [],
        }
    ],
    "inputs": [
        {
            "id": "slug",
            "type": "promptString",
            "description": "Enter the slug for the new article"
        }
    ]
}
```

# 参考
* [Zenn CLIをインストールする](https://zenn.dev/zenn/articles/install-zenn-cli)
* [GitHubリポジトリでZennのコンテンツを管理する](https://zenn.dev/zenn/articles/connect-to-github)
* [Zenn CLIで記事・本を管理する方法](https://zenn.dev/zenn/articles/zenn-cli-guide)
* [GitHubリポジトリ連携で画像をアップロードする方法](https://zenn.dev/zenn/articles/deploy-github-images)
