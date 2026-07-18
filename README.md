# mkmd-cli

git 追跡外の作業用 markdown ファイルを作成する `mktemp` ラッパー。

## インストール

`bin/` を `PATH` に通す。

```sh
git clone https://github.com/mayaton/mkmd-cli.git ~/ghq/github.com/mayaton/mkmd-cli
export PATH="$HOME/ghq/github.com/mayaton/mkmd-cli/bin:$PATH"
```

## 使い方

```sh
mkmd --dir DIR --label LABEL
```

作成されるパス（絶対パスを標準出力に返す）：

```
$MKMD_BASE_DIR/<owner>-<repo>/YYYY-MM-DD-<branch>/<DIR>/<LABEL>-<XXXXXX>.md
```

- 既定のベースディレクトリは `$XDG_STATE_HOME/mkmd`（未設定なら `$HOME/.local/state/mkmd`）
- git リポジトリ内では `origin` の owner / repo と現在のブランチ名を使う
- git 外では `local/<カレントディレクトリ名>` と `local` ブランチを使う

## 環境変数

| 変数 | 用途 |
|---|---|
| `MKMD_BASE_DIR` | ベースディレクトリの上書き（既定は `$XDG_STATE_HOME/mkmd`） |

## Claude Code に使わせる

Claude Code のグローバル設定 `~/.claude/CLAUDE.md` に以下を追記する。

````markdown
## 作業ファイル

- git で追跡されない作業ファイルは `mkmd` で作成すること（`mkmd --help` 参照）

| `--dir` | `--label` | 用途 |
|---------|-----------|------|
| `draft` | `${topic}` | 下書き・メモ |
| `research` | `${feature}-investigation` | 機能調査 |
| `plans` | `plan` | 実装計画 |
| `reviews` | `completion` | 完了確認・レビュー |
| `tmp` | `${purpose}` | 一時作業 |
````

`~/.claude/CLAUDE.md` はすべての Claude Code セッションで自動読み込みされるため、追記後は特別な起動オプションなしに `mkmd` が使われる。

## ライセンス

[MIT](LICENSE)
