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

## ライセンス

[MIT](LICENSE)
